---
title: "Error with AVCONV post reinstallation after flirtation with FFMPEG"
date: 2014-06-26
forum: Multimedia Software
---

### Post by sir-marky on 2014-06-26
Looking to solve a different problem mentioned in another thread ([http://ubuntuforums.org/showthread.php?t=2230680](http://ubuntuforums.org/showthread.php?t=2230680)) I installed ffmpeg to replace avconv on my system.
This broke video WMV playbacks causing VLC and mplayer to fall over immediately.

So I removed ffmpeg, removed the PPA and certificate and reinstalled libav-tools.

Sadly I can no longer use it.  When using the following command to convert some wav files to alac, 

```
for f in ./*.wav; do avconv -n -i "$f" -acodec alac "${f%.*}.m4a" && rm "$f"; done

```
I now receive the following multiple errors on each file, 

```
avconv version 9.13-6:9.13-0ubuntu0.14.04.1, Copyright (c) 2000-2014 the Libav developers
  built on May  9 2014 13:34:03 with gcc 4.8 (Ubuntu 4.8.2-19ubuntu1)
[COLOR=#ff0000]Unrecognized option 'n'.
Error splitting the argument list: Error number -732934152 occurred
[/COLOR]
```
The command I use IS correct.  I was using it before, albeit with warning messages in yellow.

I have tried removing, purging and reinstalling but without success.

Can anyone help me?

---

### Post by mc4man on 2014-06-26
> **sir-marky said:**
> 
```
for f in ./*.wav; do avconv -n -i "$f" -acodec alac "${f%.*}.m4a" && rm "$f"; done

```
I now receive the following multiple errors on each file, 

```
avconv version 9.13-6:9.13-0ubuntu0.14.04.1, Copyright (c) 2000-2014 the Libav developers
  built on May  9 2014 13:34:03 with gcc 4.8 (Ubuntu 4.8.2-19ubuntu1)
[COLOR=#ff0000]Unrecognized option 'n'.
Error splitting the argument list: Error number -732934152 occurred
[/COLOR]
```
The command I use [COLOR="#FF0000"]IS[/COLOR] correct.  I was using it before, albeit with warning messages in yellow.

I have tried removing, purging and reinstalling but without success.

Can anyone help me?
What is the -n supposed to do ?? (you were not using that previously

Additionally what ffmpeg did you install that 'broke' vlc or mplayer?

---

### Post by sir-marky on 2014-06-26
You are right.
I am not sure where that N variable came from.  I have  my most common commands in google keep to copy and paste and can't see  it there either.  Very weird.  My apologies.  Sometimes it's good to  have someone else point obvious things out.  I had not spotted that  variable all afternoon.

Anyone, I did remove it and the  conversions started again, albeit with additional text and colours to last time and I  now get another error at the end of each song,
```

avconv version 9.13-6:9.13-0ubuntu0.14.04.1+fdkaac, Copyright (c) 2000-2014 the Libav developers
  built on May 10 2014 17:26:31 with gcc 4.8 (Ubuntu 4.8.2-19ubuntu1)
[COLOR=#800080][wav @ 0x15d8220][/COLOR] [COLOR=#ffa500]max_analyze_duration 5000000 reached at 5015510 microseconds
Guessed Channel Layout for  Input Stream #0.0 : stereo[/COLOR]
Input #0, wav, from './15 - Eels - Mr E's Beautiful Blues.wav':
  Duration: 00:03:58.53, bitrate: 1411 kb/s
    Stream #0:0: Audio: pcm_s16le ([1][0][0][0] / 0x0001), 44100 Hz, stereo, s16, 1411 kb/s
Output #0, ipod, to './15 - Eels - Mr E's Beautiful Blues.m4a':
  Metadata:
    encoder         : Lavf54.63.104
    Stream #0:0: Audio: alac (alac / 0x63616C61), 44100 Hz, stereo, s16p, 128 kb/s
Stream mapping:
  Stream #0:0 -> #0:0 (pcm_s16le -> alac)
Press ctrl-c to stop encoding
[COLOR=#ff0000]./15 - Eels - Mr E's Beautiful Blues.wav: End of file
Error while filtering.
[/COLOR]size=   26975kB time=238.61 bitrate= 926.1kbits/s    
video:0kB audio:26964kB global headers:0kB muxing overhead 0.040980%
```

I have also noticed the version of Lavf is different to before the introduction of ffmpeg to the system.

---

### Post by mc4man on 2014-06-26
> **sir-marky said:**
> 
I have also noticed the version of Lavf is different to before the introduction of ffmpeg to the system.
Lavf54.63.104  is not the libavformat version for avconv version 9.13-6:9.13-0ubuntu0.14.04.1 (would be  Lavf54.20.4

So again, where did you get this ffmpeg package(s)  from?

---

### Post by sir-marky on 2014-06-26
The PPA I used was this one.

[https://launchpad.net/~jon-severinsson/+archive/ffmpeg](https://launchpad.net/~jon-severinsson/+archive/ffmpeg)

---

### Post by mc4man on 2014-06-26
> **sir-marky said:**
> The PPA I used was this one.

[https://launchpad.net/~jon-severinsson/+archive/ffmpeg](https://launchpad.net/~jon-severinsson/+archive/ffmpeg)
That ppa's ffmpeg packages install new shared libav libraires that 'apparently' may not be compatible with the vlc & mplayer packages you use.
(it's close enough in version to trusty's libav so doesn't seem to affect the use of avconv

Overall I can't see the reason to replace these 'system' shared libs, there is almost nothing to gain & possibly some things to break.
I'd suggest you either re-enable the ppa,  then use ppa-purge to get back to trusty packages or simply remove all the current libav packages, update your sources & then re-install as desired.
(- it would appear that at least libavformat & libavcodec are still at the ppa packages..

(- *if in fact* that ppa's ffmpeg shared libs break the current trusty vlc, mplayer, whatever then the ppa should be providing replacement builds of the affected sources.

If down the road you want a current FFmpeg  for encoding/decoding from the ffmpeg binary then use what I have [here]("https://launchpad.net/~mc3man/+archive/trusty-media"). It has no shared libs, is installed out of ld path to /opt/ffmpeg The binaries of ffmpeg, ffplay & ffprobe are run as usual as they are symlinked to /usr/bin

---

### Post by sir-marky on 2014-06-27
That fixed it.
Thank you.

I added the PPA again with,

```
sudo apt-add-repository ppa:jon-severinsson/ffmpeg
```

I then updated the repositories with,

```
sudo apt-get update
```

And then uninstalled the repository with,

```
sudo ppa-purge ppa:jon-severinsson/ffmepg
```

The system reported then removed and downgraded the library files accordingly and put me back where I was before the ffmpeg installation began.

```
Updating packages lists
PPA to be removed: jon-severinsson ffmpeg
Package revert list generated:
 libav-tools/trusty libavcodec-extra/trusty libavcodec-extra-54:amd64/trusty 
libavdevice53:amd64/trusty libavfilter3:amd64/trusty libavformat54:amd64/trusty 
libavresample1:amd64/trusty libavutil52:amd64/trusty libpostproc52:amd64/trusty 
libswresample0:amd64/trusty libswscale2:amd64/trusty

Disabling jon-severinsson PPA from 
/etc/apt/sources.list.d/jon-severinsson-ffmpeg-trusty.list
Updating packages lists
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Release &#8216;trusty&#8217; for &#8216;libswresample0&#8217; was not found
Unable to find an archive "trusty" for the package "libswresample0"
Unable to find an archive "trusty" for the package "libswresample0"
The following packages will be DOWNGRADED:
  libavcodec-extra libavcodec-extra-54 libavdevice53 libavfilter3 
  libavformat54 libavresample1 libavutil52 libpostproc52 libswscale2 
0 packages upgraded, 0 newly installed, 9 downgraded, 0 to remove and 0 not upgraded.
Need to get 3,613 kB of archives. After unpacking 2,100 kB will be freed.
The following packages have unmet dependencies:
 libswresample0 : Depends: libavutil52 (>= 7:1.2.5~) but 6:9.13-0ubuntu0.14.04.1+fdkaac is to be installed.
The following actions will resolve these dependencies:

     Remove the following packages:
1)     libswresample0              



Accept this solution? [Y/n/q/?] y
The following packages will be DOWNGRADED:
  libavcodec-extra libavcodec-extra-54 libavdevice53 libavfilter3 
  libavformat54 libavresample1 libavutil52 libpostproc52 libswscale2 
The following packages will be REMOVED:
  libswresample0{a} 
0 packages upgraded, 0 newly installed, 9 downgraded, 1 to remove and 0 not upgraded.
Need to get 3,613 kB of archives. After unpacking 2,302 kB will be freed.
Do you want to continue? [Y/n/?] y

```

I tried the conversion with AVCONV again afterwards and it reported to me the same yellow warning messages as before but no errors in red.  

Thank you for your help.

---

