---
title: "Can anybody help me play mp4 files on mplayer? :)"
date: 2010-03-20
forum: Multimedia Software
---

### Post by tillyxoxox on 2010-03-20
Whenever I try to play mp4 files on mplayer it comes up with a box that says 'Error! Cannot find codec for audio format 0x6134706D'. :( I'd be really grateful if anyone knew how to fix it! Thank you! xo

---

### Post by Surkow on 2010-03-20
What version of MPlayer and Ubuntu are you using? That error message means that MPlayer is not compiled with faad support (for MPEG4 audio support).

---

### Post by rory526 on 2010-03-20
Have you downloaded and installed the w32codecs package from medibuntu.org?

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

to summarize the commands in their how-to for 32-bit:

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
``` 

and then:

```
sudo apt-get install w32codecs
```

you might like to install a package to allow you to watch encrypted DVDs also:

```
sudo apt-get install libdvdcss2
```

---

### Post by andrew.46 on 2010-03-20
Hi tillyxoxox,

Sounds a little odd as if the file contains aac audio this is catered for quite nicely with *ffaac* as the default as well as *faad*:

```

andrew@skamandros~$ mplayer -ac help | grep -i aac
ffaac       ffmpeg    working   FFmpeg AAC (MPEG-2/MPEG-4 Audio)  [aac]
faad        faad      working   FAAD AAC (MPEG-2/MPEG-4 Audio)  [libfaad2]
```

So I guess there is either something wrong with your copy of MPlayer or possibly something unusual with the file itself. Could you post the actual file somewhere and as Surkow has asked give your version of MPlayer and Ubuntu? MPlayer version can be seen:

```
andrew@skamandros~$ **[COLOR="Red"]mplayer | head -n 1[/COLOR]**
MPlayer SVN-r30940-4.3.3 (C) 2000-2010 MPlayer Team
```

All the best,

Andrew

---

