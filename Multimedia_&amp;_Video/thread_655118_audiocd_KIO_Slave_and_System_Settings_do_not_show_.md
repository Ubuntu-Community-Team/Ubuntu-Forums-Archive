---
title: "audiocd:/ KIO Slave and System Settings do not show MP3 options"
date: 2007-12-31
forum: Multimedia &amp; Video
---

### Post by jsstumpf on 2007-12-31
Kubuntu 7.10.

I have followed the instructions for Restricted Formats installing the kubuntu-restricted-extras package.  I am able to play MP3s in amarok but I am not able to use the audiocd:/ KIO slave for MP3 (or FLAC for that matter).  I only have Ogg and CDA options beyond the .wav files.  I also cannot see MP3 tabs under "System Settings -> Advanced -> Audio Encoding".  I only have an "Ogg Vorbis Encoder" tab.

All the numerous packages are installed - the most cited being libxine1-ffmpeg.

I have rebooted at least once since the last package install.

Is there some other switch I must turn to enable these features?

Thanks in advance.

- jss

---

### Post by HakanS on 2008-01-24
I have the same problem. It worked in Fiesty

---

### Post by daiwai on 2008-05-12
I had the same problem and was able to solve it by installing the "lame" package. I know it is an old thread but maybe it still helps somebody.

```
sudo apt-get install lame
```

---

