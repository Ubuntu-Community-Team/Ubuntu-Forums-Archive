---
title: "WMAP audio for AMD64"
date: 2009-02-08
forum: Multimedia Software
---

### Post by Nais on 2009-02-08
Is there any way to get videos with WMAP (Windows Media Audio Pro) encoded audio to play with sound under a 64-bit Ubuntu Intrepid? I'm currently using VLC but I don't mind having to use another player. W32codecs is installed.

---

### Post by ssri on 2009-09-02
Try installing mplayer svn from this ppa:

[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

Worked for me on my kubunty jaunty x86_64 install.  I  wish I found this ppa earlier.  Compiling mplayer is a PITA.

---

### Post by AndyBoy_LV on 2010-05-21
> **ssri said:**
> Try installing mplayer svn from this ppa:

[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

Worked for me on my kubunty jaunty x86_64 install.  I  wish I found this ppa earlier.  Compiling mplayer is a PITA.

Thank you so much :)) Just found your post and it really solved my problem!

---

### Post by andrew.46 on 2010-05-21
Hi,

Some may be interested to know that you can test your own copy of MPlayer to look for FFmpeg's wmapro decoder as follows:
```

andrew@skamandros~$ mplayer -ac help | grep wmapro

ffwmapro    ffmpeg    untested  WMA Pro audio (FFmpeg)  [wmapro]
```

and yes this will work on 64 bit Ubuntu, you just need a fairly recent copy, preferably the latest svn...

Andrew

---

### Post by hhh81 on 2010-05-24
Thanks
```
enrico@ubuntu:/$ mplayer -ac help | grep wmapro
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
ffwmapro    ffmpeg    untested  WMA Pro audio (FFmpeg)  [wmapro]

```

wmv wmap video and audio are ok in mplayer
MPlayer SVN-r31042-Ubuntu-RVM (C) 2000-2010 MPlayer Team

moreover this command
```
sudo apt-get purge bluez-alsa
```

to remove 
bt_audio_service_open: connect() failed: Connection refused (111)
error

---

### Post by hg21 on 2010-07-16
> **ssri said:**
> Try installing mplayer svn from this ppa:

[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

Worked for me on my kubunty jaunty x86_64 install.  I  wish I found this ppa earlier.  Compiling mplayer is a PITA.

Many thanks ssri.  Worked great for me.

---

