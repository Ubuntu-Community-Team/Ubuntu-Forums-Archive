---
title: "Does RealPlayer use oss or esd ??"
date: 2006-11-06
forum: Multimedia &amp; Video
---

### Post by phil79 on 2006-11-06
Can someone please tell me ???

I'm trying to fix why real player audio on a "server" does not play on the "client" via nxclient.....

Thanks.

---

### Post by phil79 on 2006-11-06
I did some RTFM :-)

The RealPlayer README says....

" Alsa and esound drivers are not
  included in this build
  * The OSS device used for playback can
  be set using the AUDIO environment
  variable.
  + eg export AUDIO=/dev/dsp2"

Can someone please help me on this ????

On my "server"  - when RealPlayer is NOT running - I have:

ubuntu:/opt/helixPlayer> lsof /dev/dsp
ubuntu:/opt/helixPlayer>

And when running RealPlayer I have:

ubuntu:/opt/helixPlayer> lsof /dev/dsp
COMMAND     PID   USER   FD   TYPE DEVICE SIZE NODE NAME
realplay. 31094 philip   16w   CHR   14,3      9555 /dev/dsp


I also have:

ubuntu:/opt/helixPlayer> ps aux|grep esd
philip    5500  0.0  0.2   5872  4232 ?        Ss   Nov04   0:00 /usr/bin/esd -terminate -nobeeps -as 1 -spawnfd 18

Don't know what to do now....

Wish RealPlayer would use esd.....do older versions use esd ???

About to give up, but just the odd clue would be nice ](*,) 

Thanks

---

