---
title: "Ubuntu 8.10: Amarok, Can't use 5.1 speaker Arrangement"
date: 2009-01-31
forum: Multimedia Software
---

### Post by chronosoft on 2009-01-31
Hey guys ;) I Can't seem to get Amarok to use the 5.1 speaker arrangement (there are only 2 speakers being used) 

Here are my specs
AMD Athlon(tm) 64 X2 Dual Core Processor 6000+
4gigs DDR II 800 ram
Ubuntu 8.10
nvidia 9600GT
Creative audigy value sound card

I have included a picture that could better explain my problem better. Thanks in advance
**P.S.** when the speaker arrangement box is selected, a selection box doesn't drop down with options, just thought to clarify.

[[IMG]http://img218.imageshack.us/img218/9677/19049921ky7.th.png[/IMG]](http://img218.imageshack.us/my.php?image=19049921ky7.png)

---

### Post by markbuntu on 2009-02-01
Since you are using pulseaudio as your sound server. you need to change its default from 2 channels to 6 for 5.1 sound. To do this edit the file

/etc/pulse/daemon.conf

look for the line 

;default-sample-channels = 2

change it to 

default-sample-channels = 6

 for 5.1 sound. Save the file and restart pulseaudio

killall pulseaudio

pulseaudio -D

---

### Post by mc4man on 2009-02-03
@chronosoft

As per that message of a few days ago  the 2 to 6 seems to be the standard solution, if that's working out, great, if your not totally thrilled with the potential downsides to pulse doing the upmixing let me know. 
I started fresh and have, imo, better sound quality and upmixing to 6 ch from all types/formats of audio sources without the 2 -6 bit.

---

