---
title: "Musepack SV8 howto playback with Rhythmbox/vlc/etc?"
date: 2009-03-24
forum: Multimedia Software
---

### Post by monkman on 2009-03-24
Hi, what have i to do, to listen to mpc files which are encoded with the latest muepack codec SV8 using rhythmbox(or any other player)? Do i have to wait until gstreamer gets the necessary updates? Thx!!!

---

### Post by andrew.46 on 2009-03-24
Hi,

I believe that both the newest MPlayer and FFplay will both play these files:

```

andrew@skamandros~$ mplayer -ac help | grep mpc

ff4xmadmpcm ffmpeg    working   FFmpeg 4XM ADPCM audio  [adpcm_4xm]
ffmusepack7 ffmpeg    working   Musepack sv7 audio codec  [mpc7]
**[COLOR="Red"]ffmusepack8 ffmpeg    working   Musepack sv8 audio codec  [mpc8][/COLOR]**
musepack    mpcdec    working   Musepack audio codec


```

```
andrew@skamandros~$ ffmpeg -formats | grep mpc
FFmpeg version SVN-r18169, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --prefix=/usr --mandir=/usr/man --disable-debug --enable-shared
 --disable-static --enable-postproc --enable-avfilter --enable-pthreads 
--enable-libtheora --enable-libvorbis --enable-x11grab --enable-libmp3lame 
--enable-libx264 --enable-libschroedinger --enable-libfaac --enable-libfaad 
--enable-libamr-wb --enable-libamr-nb --enable-libgsm --enable-libspeex 
--enable-nonfree --enable-gpl
  libavutil     50. 2. 0 / 50. 2. 0
  libavcodec    52.22. 3 / 52.22. 3
  libavformat   52.32. 0 / 52.32. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar 23 2009 21:47:33, gcc: 4.2.4
 D  mpc             Musepack
**[COLOR="Red"] D  mpc8            Musepack SV8[/COLOR]**
 D A    mpc7            Musepack SV7
**[COLOR="Red"] D A    mpc8            Musepack SV8[/COLOR]**
```

So I guess you could try either of these, the svn MPlayer being the obvious better choice as FFplay is funnctional but fugly :-). I tested both using this file:

[http://samples.mplayerhq.hu/A-codecs/musepack/sv8/Glinka.mpc](http://samples.mplayerhq.hu/A-codecs/musepack/sv8/Glinka.mpc)

and the file played flawlessly with the usual amazing mpc sound that is sadly appreciated by so few.

All the best,

Andrew

---

### Post by monkman on 2009-03-25
thx.... this would be a big loss of comfort to me, so i think i just wait a while...

---

### Post by andrew.46 on 2009-04-01
Hi,

Oops! I have shown you the ugly side of MPlayer :-). I attach a screenshot of SMPlayer playing the same file, the gui makes life a little easier!

Andrew

---

### Post by Antonski on 2009-05-07
Unfortunately, mplayer has problems with tagged musepack sv8 files - it enters an endlss loop at the eof.

[http://bugzilla.mplayerhq.hu/show_bug.cgi?id=1458](http://bugzilla.mplayerhq.hu/show_bug.cgi?id=1458)

VLC does not play at all SV8 files :(

~~

---

### Post by andrew.46 on 2009-05-07
Hi Antonski,

> **Antonski said:**
> Unfortunately, mplayer has problems with tagged musepack sv8 files - it enters an endlss loop at the eof.

[http://bugzilla.mplayerhq.hu/show_bug.cgi?id=1458](http://bugzilla.mplayerhq.hu/show_bug.cgi?id=1458)


Interesting, unfortunately I cannot get hold of the sample that the bug report describes. Do you have access to this file or similar?

I might experiment on the weekend with creating and playing back a few sv8 files just for curiosity....

Andrew

---

### Post by Antonski on 2009-05-09
Hi andrew.46,

yes, I have this file on my office PC. Actually, this was just a test file (for mplayer functionality), I've tried few more. The problem appeared after tagging and only with sv8 files. 
BTW, I'm with windows, I don't know whether it will be the same with linux. I just haven't find time to install and play with ubuntu, but maybe soon I will.
~~

---

### Post by andrew.46 on 2009-05-09
Hi Antonski,

> **Antonski said:**
> yes, I have this file on my office PC. Actually, this was just a test file (for mplayer functionality), I've tried few more. The problem appeared after tagging and only with sv8 files. 

Is there any chance that you could post these files somewhere?

> BTW, I'm with windows, I don't know whether it will be the same with linux. I just haven't find time to install and play with ubuntu, but maybe soon I will.

So possibly you are using an older version of MPlayer? I am not sure how you could demonstrate the version number under windows, for linux the following works:

```

andrew@skamandros~$ mplayer | head -n1
MPlayer SVN-r29286-4.2.4 (C) 2000-2009 MPlayer Team

```

but for windows I am not sure :confused:. However I would be very interested to see one of these problem files. These forums allow 900kb zip file attachments if this would be the easiest way for you, and if you are interested in pursuing this?

All the best,

Andrew

---

### Post by andrew.46 on 2009-05-30
Hi Antonski,

> **Antonski said:**
> Unfortunately, mplayer has problems with tagged musepack sv8 files - it enters an endlss loop at the eof.

As it turns out MPlayer had a segmentation fault with the sv8 files that I made myself. I have submitted bug reports as well:

[http://lists.mplayerhq.hu/pipermail/mplayer-users/2009-May/076963.html](http://lists.mplayerhq.hu/pipermail/mplayer-users/2009-May/076963.html)
[https://roundup.mplayerhq.hu/roundup/ffmpeg/issue1131](https://roundup.mplayerhq.hu/roundup/ffmpeg/issue1131)

Just hoping that the writer of the sv8 decoder is still active.

Andrew

---

### Post by paranoiadk on 2010-12-10
Real sorry if I'm resurrecting a dead topic, but I kinda found the solution for this problem. And since it was my top result in google I though I might as well post the solution for others.
I've tried different players and they all seem to work (Aqualung, Rhythmbox, ...). Audacity crashes and I haven't tried Amarok, but since I'm happy with Rhythmbox I'm sticking with it.
Anyway, I installed a bunch of packages in synaptic:
xmms2-plugin-musepack (although I don't think this one helped, since it's for xmms)
libmpcdec6
oidua
libaudclient2 (I believe this only affect audacios)
libaudcore1  (I believe this only affect audacios)
gstreamer0.10-plugins-bad
and some audio players.

Anyway, I hope I've helped someone.

Cheers!

PDK

---

### Post by shantiq on 2010-12-10
seems to be all ok nowadays with SV8   350kbps    not a bad lossy format at all


to rip directly to musepack you can use [Rubyripper]("http://archive.getdeb.net/getdeb/ubuntu/pool/apps/r/rubyripper/") with tagging


enter this code in the other box

```
  
mpcenc --quality 10.00  --artist "%a" --title "%t" --album "%b" --genre "%g" --year "%y" -if "%i" "%o" .mpc
```



FIRST you will need to install


```
sudo apt-get install musepack-tools
```

and make the encoder executable this way

```
cd  /usr/bin
```
```
sudo chmod +x mpcenc
```

and then you are good to go

---

