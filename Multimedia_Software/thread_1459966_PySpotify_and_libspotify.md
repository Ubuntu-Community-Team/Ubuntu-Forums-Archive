---
title: "PySpotify and libspotify"
date: 2010-04-22
forum: Multimedia Software
---

### Post by boubbin on 2010-04-22
Have anyone managed to get the python wrapper to work with libspotify?
[http://developer.spotify.com/en/libspotify/overview/](http://developer.spotify.com/en/libspotify/overview/)
and
[http://github.com/winjer/pyspotify](http://github.com/winjer/pyspotify)

i keep running to these compilation failures when checking git repo...
> building 'spotify._spotify' extension
gcc -pthread -shared -Wl,-O1 -Wl,-Bsymbolic-functions build/temp.linux-i686-2.5/src/module.o build/temp.linux-i686-2.5/src/session.o build/temp.linux-i686-2.5/src/link.o build/temp.linux-i686-2.5/src/track.o build/temp.linux-i686-2.5/src/album.o build/temp.linux-i686-2.5/src/artist.o build/temp.linux-i686-2.5/src/search.o build/temp.linux-i686-2.5/src/playlist.o build/temp.linux-i686-2.5/src/image.o -Llib -lspotify -o build/lib.linux-i686-2.5/spotify/_spotify.so
/usr/bin/ld: skipping incompatible lib/libspotify.so when searching for -lspotify
/usr/bin/ld: skipping incompatible /usr/local/lib/libspotify.so when searching for -lspotify
/usr/bin/ld: cannot find -lspotify
collect2: ld:n paluuarvo oli 1
error: command 'gcc' failed with exit status 1
i know this is mroe gcc related, i think im not satifying the dep's

---

### Post by Girindor on 2010-04-28
I struggled for ages, getting Spotify to work on Ubuntu, it breaking, re-installing, etc. -until I discovered We7.com which is basically like Spotify but web-based, works like a charm, and has less annoying ads.

You're welcome :-)

---

