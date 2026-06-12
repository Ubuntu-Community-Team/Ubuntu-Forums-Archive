---
title: "Ubuntu 7.10 no sound"
date: 2008-04-15
forum: Multimedia &amp; Video
---

### Post by BeoprobUb on 2008-04-15
Hello everybody,
I start saying that I'm a nOOb... Some time ago I've tried to install Ubuntu 7.10 on my Laptop (Toshiba Equium), I have also a partition with Vista.
 Ubuntu seems to work properly and when the operative system start there's the Login sound, but when I try to listen a mp3 or when I want see a utube video there's no sound at all.
I've tried to fix the problem finding on the net similar problems but without results.

editing lspci -v on the shell I get:

...
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff40
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at ff63c000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
...

In Vista the sound card is recognized as:

soundMAX Integrated Digital HD Audio;

I hope somebody can help me!
Thank u bye

---

### Post by warp99 on 2008-04-15
Well both mp3 and flash are proprietary multimedia formats. Did you install flash and the codecs for mp3?

Edit:
If you get sound on the login, then your sound is working fine.

---

### Post by BeoprobUb on 2008-04-16
I'm not sure, now I've tried to do it again but I don't know if the procedure that I've done is correct.
First I've download from XMMS' site the last release 1.2.11, then I've unzipped the contained folder and I've tried to run all the files that were in the folder but again without results.
Yesterday I've tried to install alsa driver 1.0.16 as well as I did with 1.2.11, result:
when the computer start for some minutes I can hear the music, for example mp3 files but after a while I lose again the sound. 
Furthermore when the sound works sometimes I hear a fizz very pestering. I think this could be caused by the fact that I've tried to set the alsamixer ...

I know I'm an hopeless case but please help me!!

PS:The sound at the login continue to work (but with the fizz)

---

### Post by BeoprobUb on 2008-04-16
I forgot a thing ...
when the sound work is working just from the right speaker. :confused:

---

### Post by Yellow Pasque on 2008-04-16
Try these scripts and also look at the link about configuring the alsa-base file.
[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)

---

### Post by BeoprobUb on 2008-04-16
> **Temüjin said:**
> Try these scripts and also look at the link about configuring the alsa-base file.
[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)

I've tried to do it and now also the login sound that before was working is not working any more ... :(
I've also rebooted twice like is written

---

### Post by BeoprobUb on 2008-04-16
I haven't try to configure the alsa-base ... could be this the problem?

---

### Post by BeoprobUb on 2008-04-16
I'm sorry ....
It works!!!!!
Thank you very much!!!!!

---

