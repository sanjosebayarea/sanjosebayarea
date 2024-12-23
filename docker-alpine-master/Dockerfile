FROM alpine:3.16
RUN apk add --no-cache lua5.3 lua-filesystem lua-lyaml lua-http
# Create non-root user and set permissions
RUN (which useradd || apk add --no-cache shadow) && \
    (useradd -u 1000 appuser || true) && \
    chown -R 1000:1000 /usr/local/bin/fetch-latest-releases.lua
COPY fetch-latest-releases.lua /usr/local/bin
VOLUME /out
USER 1000
ENTRYPOINT [ "/usr/local/bin/fetch-latest-releases.lua" ]
