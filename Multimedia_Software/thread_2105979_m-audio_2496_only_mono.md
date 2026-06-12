---
title: "m-audio 2496 only mono"
date: 2013-01-17
forum: Multimedia Software
---

### Post by dirty_harry on 2013-01-17
Hello,

I can not find the switch/option enable stereo! My m-audio 2496 only functions mono for input and output! 
I am using mudita24 to control my snd card. 

```

$> cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
$> uname -a
Linux fastbumm 3.2.0-35-generic #55-Ubuntu SMP Wed Dec 5 17:42:16 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
$> lspci | grep audio
03:00.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)

```

thanks

---

### Post by tgalati4 on 2013-01-17
I don't have this card, but it looks like you have 2 stereo channels and you have the "gang" buttons pushed which merge the channels to make 2 mono signals.  Ungang them and should have 2 stereo channels.

---

### Post by dirty_harry on 2013-01-17
I tried what you suggested, but ungang seems to have no effect. I've used ubuntustudio 12.04 live to try it out in a different install, sadly no change.

I will try to install windows to try it out in a native environment.

---

### Post by tgalati4 on 2013-01-17
What kind of cables are you using to connect to the inputs?  You need to used balanced (ring,tip,sleeve) style cables for each stereo channel, not guitar cables.

---

### Post by dirty_harry on 2013-01-18
My mixer is connected via cinch. The mixer output is 6.3 audio jack. I have to use several adapters, but I connected it directly to my speakers(aux in) and everything works. Maybe the 2496 got bricked?!

I will try a different installation, but now I am off to my day-job 8-)

---

