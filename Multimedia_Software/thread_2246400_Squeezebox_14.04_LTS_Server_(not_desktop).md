---
title: "Squeezebox 14.04 LTS Server (not desktop)"
date: 2014-09-30
forum: Multimedia Software
---

### Post by rick36 on 2014-09-30
I have successfully installed and am currently using logitechmediaserver on Ubuntu "Desktop" 14.04.

```
# dpkg --list | grep -i logitech
ii  logitechmediaserver               7.9.0~1409327717                    all          Streaming Audio Server
```

I would like to install it on the server version Ubuntu 14.04.1 LTS [server] edition. *If you REALLY need to know why, please PM, don't want to fill this thread with off-topic chatter.*

I tried to install logitechmediaserver 7.9 on 14.04 server, but could not get any audio to work.

I'm not sure what audio libraries, codecs etc etc I need to install to make it work.  I installed ALSA, but still, nothing.  Logitech media server logs would report "Unable to play mp3 stream from http://some.radio.station.com"  That indicates lame, but /bin/lame existed.

I'm using the dpkg --install [lms].pkg file to install, not apt-get.  As the version it installs using apt-get does not work due to perl incompatibilities.

Anyone know what libraries/codecs/supporting programs are needed for a successful install on the 'server' version, not the desktop version?

Thanks!

---

