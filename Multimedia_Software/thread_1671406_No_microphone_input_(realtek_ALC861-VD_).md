---
title: "No microphone input (realtek ALC861-VD )"
date: 2011-01-20
forum: Multimedia Software
---

### Post by piratelv on 2011-01-20
Hello every one,
I know this question has been asked many many times (because I did search) but I can not find an answer that solve my problems.

The problem i'm having is that my microphone stopped working after the upgrade to 10.10. Ubuntu doesn't seen any sort of input device any more, no line-in , no mic ( front as back ).

Own on to the specs of my machine:
[LIST]
[*]It has a realtek ALC861-VD audio chip
[*]2 mic jacks, 1 line-in , 2 out (front and back) and a coaxial port thing :?
[*]The os is a upgraded from 10.04 to 10.10 and everything except this and my tv card sound works.
[*]I have pulse audio tools and alsa mixer ( although it broke during upgrade ) installed.
[*]alsa info is available upon request, so is any other info may you need it.
[/LIST]

I hope some one can fix my microphone i really really appreciate it.

---

### Post by piratelv on 2011-01-23
Small bump.
I really would like a suggestion, idea, fix for my issue.
Does nobody have a clue?

---

### Post by xc3RnbFO8P on 2011-01-23
Read this:
[http://forums.linuxmint.com/viewtopic.php?f=48&t=60979]("http://forums.linuxmint.com/viewtopic.php?f=48&t=60979")

---

### Post by piratelv on 2011-01-25
> **Ringi said:**
> Read this:
[http://forums.linuxmint.com/viewtopic.php?f=48&t=60979]("http://forums.linuxmint.com/viewtopic.php?f=48&t=60979")
Thanks for the reply, This unfortinatly didn't help me. I do see the alsa capture in the alsa mixer but it outputs nothing.
When I look at the recording volume from puvdev the bars just pulsate.

Al thought my problem is very close to that of the thread you linked the solution for it did not resolve my issues.

If you or any one have any other idea's I can try pretty much everything since this is not my first difficulties on this terrain.

---

### Post by piratelv on 2011-02-01
It's been a while again. I can't and will not believe no one has clue. So another bump. :(

---

### Post by nowardev on 2011-03-07
hi there i have alc861-vd on toshiba laptop and... i use kubuntu 
i have fixed using this 

options snd-hda-intel model=lenovo



ALC861VD/660VD
==============
3stack	3-jack
3stack-dig	3-jack with SPDIF OUT
6stack-dig	6-jack with SPDIF OUT
3stack-660	3-jack (for ALC660VD)
3stack-660-digout 3-jack with SPDIF OUT (for ALC660VD)
lenovo	Lenovo 3000 C200
dallas	Dallas laptops
hp	 HP TX1000
asus-v1s	ASUS V1Sn
auto	 auto-config reading BIOS (default)
so now you have to edit this file
kdesudo kate /etc/modprobe.d/alsa-base.conf
and add (end of file ) for example
options snd-hda-intel model=lenovo position_fix=0
position_fix can be &#8212;-> 0 1 2 3

---

### Post by techman2go on 2011-03-21
I have a similar problem and would also like a solution.   I have two drives in a Dell Dimension 3000.   I can boot to Windows XP and the mic in works great.   I boot to Ubuntu 10.10 and there is not mic.  I boot to Kubuntu 10.10 and there is no mic.   The system does not see any device there.   

Windows says it is a Sound Max Integrated Digital Audio device manufactured by Creative Technology, Inc.
I used the aplay command and it reports the audio device as Intel ICH5, device 0, with a media controller as Intel 82801EV/ER (ICH5/ICH5R)  AC'97 Rev 2,  Dell Device 019d

I can play sound out thru the speakers fine.   It is only the input mic that does not work.   Works under Windows XP but not under Ubuntu 10.10.   

Any suggestions?   Thanks.:confused:

---

### Post by techman2go on 2011-03-21
I solved my problem.   User error.  Some how I set the hardware in the sound preference to input only.   So I went to Systems > Preferences > Sound and selected the Hardware tab.   I then selected "Analog Stereo Duplex" and in the input pane I selected "Analog Microphone / Microphone 1" and I got sound input.   Seems if you tell the system the hardware only has an output then it will never see an input.  It also works if you select mic 2.  ):P

---

