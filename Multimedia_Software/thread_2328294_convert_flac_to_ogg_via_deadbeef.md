---
title: "convert flac to ogg via deadbeef"
date: 2016-06-19
forum: Multimedia Software
---

### Post by czgirb on 2016-06-19
currently i'm using **ubuntu 14.04LTS** & **deadbeef 0.7.2**

by using a guidance from: [http://askubuntu.com/questions/206191/how-to-convert-audio-files-in-deadbeef-player](http://askubuntu.com/questions/206191/how-to-convert-audio-files-in-deadbeef-player)
in order to **convert flac to ogg via deadbeef**, i used this command:
```
sudo apt-get install vorbis-tools
```
**my question is:**
how can i know which ogg was installed? **ogg AoTuV** or **ogg libVorbis**?
how can i check it via terminal?
[B]thank you
[/B]

---

### Post by ron998 on 2016-06-19
> **czgirb said:**
> **my question is:**
how can i know which ogg was installed? **ogg AoTuV** or **ogg libVorbis**?
how can i check it via terminal?
Hi
**mediainfo** program will show that the repository version of vorbis-tools isn't compiled using the aoTuV library.
```
[SIZE=2]@Xubuntu:~$ mediainfo foo.ogg
General
Complete name                            : foo.ogg
Format                                   : OGG
File size                                : 782 KiB
Duration                                 : 1mn 0s
Overall bit rate mode                    : Variable
Overall bit rate                         : 106 Kbps

Audio
ID                                       : 896091583 (0x356945BF)
Format                                   : Vorbis
Format settings, Floor                   : 1
Duration                                 : 1mn 0s
Bit rate mode                            : Variable
Bit rate                                 : 112 Kbps
Channel(s)                               : 2 channels
Sampling rate                            : 44.1 KHz
Compression mode                         : Lossy
Stream size                              : 827 KiB
Writing library                          : [/SIZE][COLOR=#ff0000][SIZE=2]libVorbis (Schaufenugget) (20101101 (Schaufenugget))[/SIZE]
[/COLOR]

```

**mediainfo** program shows a different result when vorbis-tools is compiled using the aoTuV library.
```
[SIZE=2]@Xubuntu:~$ mediainfo foo.ogg
General
Complete name                            : foo.ogg
Format                                   : OGG
File size                                : 808 KiB
Duration                                 : 1mn 0s
Overall bit rate mode                    : Variable
Overall bit rate                         : 109 Kbps

Audio
ID                                       : 347075555 (0x14AFF3E3)
Format                                   : Vorbis
Format settings, Floor                   : 1
Duration                                 : 1mn 0s
Bit rate mode                            : Variable
Bit rate                                 : 112 Kbps
Channel(s)                               : 2 channels
Sampling rate                            : 44.1 KHz
Compression mode                         : Lossy
Stream size                              : 827 KiB
Writing library                          : [COLOR=#008000]aoTuV 20110424 (UTC 2011-04-24)[/COLOR][/SIZE]

```

---

### Post by mc4man on 2016-06-19
I believe since libvorbis-1.3.2 the AoTuV changes were & [have been merged]("http://www.geocities.jp/aoyoume/aotuv/").

---

### Post by czgirb on 2016-06-20
> **mc4man said:**
> I believe since libvorbis-1.3.2 the AoTuV changes were & [have been merged]("http://www.geocities.jp/aoyoume/aotuv/").

libvorbis 1.3.2 ... start from when?
if it was installed libvorbis (previous version), is ubuntu will automatically update the version or no?
how can i update it to the latest version?
when i'm using a deadbeef to convert the flac file into ogg, is it possible from me the choose what ogg is desired?

---

### Post by Yellow Pasque on 2016-06-20
```
apt-cache policy libvorbis0a
```

Trusty is using libvorbis 1.3.2

> if it was installed libvorbis (previous version), is ubuntu will automatically update the version or no?

The latest upstream version? No.

> how can i update it to the latest version?

You would use a PPA (if one existed) or build libvorbis and vorbis-tools yourself. Considering that the changes between 1.3.2 and 1.3.5 are very minor and none are related to audio quality, that would be a lot of hassle for little/no gain.

> when i'm using a deadbeef to convert the flac file into ogg, is it possible from me the choose what ogg is desired? 

It's been a long time since I looked at deadbeef, but I'm guessing it just uses oggenc as a backend rather than doing its own special ogg encoding. In other words, no, you can't easily choose the version.

---

### Post by czgirb on 2016-06-20
Thank you for everybody who has been participate to give me a guidance
**thank you**

---

