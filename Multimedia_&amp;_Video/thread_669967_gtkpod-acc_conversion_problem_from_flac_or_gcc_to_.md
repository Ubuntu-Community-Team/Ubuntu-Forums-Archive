---
title: "gtkpod-acc conversion problem from flac or gcc to mp3."
date: 2008-01-16
forum: Multimedia &amp; Video
---

### Post by tridhavee on 2008-01-16
When I try to transfer flac or gcc files from Ubuntu 7.10 on thinkpad x61 to ipod I get converting error:
failed: '/usr/share/gtkpod-aac/scripts/convert-ogg2mp3.sh' returned exit status 4.

same error with convert-flac2mp3.sh

anyone know a fix?

---

### Post by tridhavee on 2008-01-16
I'm also using gtkpod to do this transfer.

---

### Post by pont on 2008-01-27
if  '/usr/share/gtkpod/scripts/convert-ogg2mp3.sh' returned exit status 4 then you have to install oggdec, located in the vorbis-tools package.

```
apt-get install vorbis-tools
```

if  '/usr/share/gtkpod/scripts/convert-ogg2mp3.sh' returned exit status 5. then you must install lame.

```
apt-get install lame
```

---

### Post by duphenix on 2008-03-01
for exit code 4 you need to install the flac package


apt-get install flac

---

### Post by timbosity on 2008-03-25
Just a quick note here to say ta i thought I had flac installed seeing I could play flac files in xmms but it appears I didnt and it did indeed fix all problems.:guitar:

---

