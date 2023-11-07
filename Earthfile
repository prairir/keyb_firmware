VERSION 0.7

pull-zmk:
    FROM alpine/git:latest

    RUN git clone https://github.com/moergo-sc/zmk.git src

    SAVE ARTIFACT src

build:
    FROM nixos/nix:master

    WORKDIR /dir
    COPY +pull-zmk/src ./src

    COPY . .
    COPY --dir config/ ./

    RUN nix-build config -o combined

    SAVE ARTIFACT combined/glove80.uf2 AS LOCAL glove80.uf2
