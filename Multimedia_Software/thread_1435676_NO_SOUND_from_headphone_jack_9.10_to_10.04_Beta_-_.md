---
title: "NO SOUND from headphone jack? 9.10 to 10.04 Beta - was working before upgrade?"
date: 2010-03-21
forum: Multimedia Software
---

### Post by mrebanza on 2010-03-21
Ok so I have a new Toshiba Laptop I bought about a month or two ago and It's dual booting Ubuntu and Win7 - I was running Ubuntu 9.10 and deciede I would give Ubuntu 10.04 Beta a try . . . So I copied my files over to the win7 partition and deleted ubuntu9.10 and installed 10.04 beta . . . 


Now ubuntu wont recognize the headphone input jack? 

I tried going into the sound setting and it is simply not their?

I tried installing ubuntu restricted extras - reboot - didn't help

Are their any other driver or something else that I am missing that I can install

Like I said It was working perfectly before 10.04???

(besides the fact that the headphone jack and the internal speakers used to play simultaneously but I kind of liked that anyway because my PC speakers aren't all that loud to begin with )


Anybody else having this problem?!?!?!?!?!    :confused:

---

### Post by JC Cheloven on 2010-03-21
Seems to be a bug. 
I also had problems with sound with lucid alpha 3 (I tried to stop pulseaudio with "pulseaudio -k", and never got sound again with "pulseaudio -D"). It's a different one, but anyway.

Let's hope the best for the main release.

---

### Post by RedSingularity on 2010-03-21
Do you have sound at all?

---

### Post by mrebanza on 2010-03-21
> **RedSingularity said:**
> Do you have sound at all?

Yea the built in speakers work perfectly fine . . . it is the input of speakers/headphones than seem to be the problem . . . the headphone jack doesn't seem to be recognized by ubuntu as far as i can tell . . . like I said both headphone jack and internal speakers were **BOTH **working perfectly fine on **9.10?!?!** . . . problem only after fresh install of 10.04 beta . . .

---

### Post by RedSingularity on 2010-03-21
Check in the alsamixer and see if the levels are up.

In terminal type 

alsamixer

---

### Post by Franbugallo on 2010-03-23
Have the same issue. Everything is fine in alsamixer. Still no sound from headphone jack. Some help please

---

### Post by mrebanza on 2010-03-23
> **Franbugallo said:**
> Have the same issue. Everything is fine in alsamixer. Still no sound from headphone jack. Some help please
[http://www.linuxant.com/drivers/](http://www.linuxant.com/drivers/) : You can get a "riptide" driver.  According to another forum, it works. I will give it a try and let your guys know -  this is supposed to work of the Conexant Audio driver that is distributed with my Toshiba Laptop - do you also have a toshiba Franbugallo?

---

### Post by mrebanza on 2010-03-23
[http://ubuntuforums.org/showthread.php?t=495330](http://ubuntuforums.org/showthread.php?t=495330)

In this thread someone is recommending you Download the "Alsa-Driver (1.0.14 - no RC's!)"

and to tell you the truth I this I have read that thread and done it before!?!?! hahaha


I think that is how I got the audio working correctly on the toshiba in the first place . . . but I can't be sure anyway try that first . . . as am I . . . and let us know how it goes;)

---

### Post by Franbugallo on 2010-03-23
I have a toshiba as well. Mine is a little bit older (almost 3 years) my sound card is an ALC 268.

I can't try any of the solutions now. I had made a very big mistake and have to made a full reinstall. Tell me if any or both of the solutions work please.
Thanks

---

### Post by edwardtilbury on 2010-03-23
Same problem here.. 

Actually, I have 10.04 Beta 2 x64 on my Toshiba P105-S9339 , sound was working well.. did an upgrade... reboot... Hey what's that guy saying in the YouTube video? AHHH NO SOUND!

Checked alsa in Terminal and also in GUI , looks fine.. what gives?

I'll try these solutions and post the result.

---

### Post by edwardtilbury on 2010-03-23
I did the following to fix the sound on my Toshiba P105-S9339 Ubuntu 10.04 x64 Beta 1:
( Conexant CX20549 (Venice)  chip according to 'alsamixer'  )



Synaptic Package Manager:

Searched for and installed this package:

linux-backports-modules-alsa-2.6.32-16-generic



... Reboot and see if that works?

Also I installed this so I'm not sure if this was what helped it work:

[http://www.linuxant.com/alsa-driver/downloads-ubuntu-x86_64.php](http://www.linuxant.com/alsa-driver/downloads-ubuntu-x86_64.php)

It's an easy .deb 1 click install after you unzip it.. 



Maybe it was the combination of both things, but I have my sound now :)

---

### Post by mrebanza on 2010-03-26
The Kernel version on Ubuntu 10.04 Beta is 2.6.32-16-generic

The sound driver list on linuxant only goes up to 2.6.28-15-generic - Am I missing something?

[http://www.linuxant.com/alsa-driver/downloads-ubuntu-x86_64.php](http://www.linuxant.com/alsa-driver/downloads-ubuntu-x86_64.php)

---

### Post by mrebanza on 2010-03-26
Ok I am gonna try a generic package see if it works - about to reboot - wish me luck :popcorn:

[http://www.linuxant.com/alsa-driver/downloads.php#generic](http://www.linuxant.com/alsa-driver/downloads.php#generic)

---

### Post by Franbugallo on 2010-04-14
Any news? Works any solution?

---

### Post by mrebanza on 2010-04-14
No luck so far for me . . . I ended up switching back to Ubuntu 9.10 Karmic for now . . . sucks because I enjoy the SUPER FAST boot time in ubuntu 10.04 . . . but he hopefully it will be fix in the official 10.04 release

on a side note I have install Ubuntu 10.04 on two other laptops (One Acer and a Gateway all 2010 Win7z) and a Sony Desktop and all sound cards worked perfectly . . Toshiba laptops are rather propitiatory I guess . . . idk . . .  try 


sudo apt-get install ubuntu-restricted-extras

---

### Post by Franbugallo on 2010-04-18
I found this, maybe it will be useful when solved

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/553002](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/553002)

---

### Post by Yellow Pasque on 2010-04-18
> **mrebanza said:**
> [http://ubuntuforums.org/showthread.php?t=495330](http://ubuntuforums.org/showthread.php?t=495330)
In this thread someone is recommending you download the "Alsa-Driver (1.0.14 - no RC's!)"
That section of the sticky is woefully outdated (I've requested the forum staff replace it with a link to the ALSA upgrade script I reference below). 

What specific Toshiba laptop and audio codec do you have? What is the output of:
```
aplay -l
```

I would use the ALSA upgrade script:
[http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)
Before you run it, make sure you edit the script to get the latest ALSA (1.0.23):
```
PACKAGE=1.0.23

setpack () {
DRIVER=alsa-driver-1.0.23
FIRMWARE=alsa-firmware-1.0.23
LIB=alsa-lib-1.0.23
PLUGINS=alsa-plugins-1.0.23
UTILS=alsa-utils-1.0.23
TOOLS=alsa-tools-1.0.23
OSS=alsa-oss-1.0.17
}
```

Then, if you have a Satellite M300:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
Add this line to the end of the file:
```
options snd-hda-intel model=toshiba
```
Save. Quit. Reboot.

---

### Post by Franbugallo on 2010-04-19
This is the first solution that actually works!!!!
Thank you very much
There's only a issue....the volume trough jack is terrible low. I'll try to find is everything is ok with the mixers....

---

### Post by Franbugallo on 2010-04-20
after a long search. I found everything is okay. So, no reason why such a low volume. Anyone?
Thanks

---

### Post by Franbugallo on 2010-04-22
Ok! Problem completely solved with Temüjin but adding this line to alsa.conf

options snd-hda-intel model=3stack

I have an A200 Toshiba

---

### Post by RationalGaze on 2010-04-25
Hello!

I have the same problem. I've tried all solutions posted in this thread, and none of them works :confused:. 
I have a Toshiba A200 with a ALC861VD sound card and running ubuntu 10.04. Currently i have 1.0.22 version of ALSA (tried also with 1.0.23, with no success..). Sound works on speakers, but plugging the headphones in has no effect. Also manually changing the output in sound preferences to a"nalog headphones" doesn't help. It only mutes the speakers..

It worked in 9.10. But it is strange, three days ago i installed 10.04, saw that the sound wasn't working, and again went back to 9.10. On that second 9.10 install i had the same problem! But about 6 months ago, on my first 9.10 install, sound worked out of the box. This is really bothering me...

Any suggestions?

Thanks.

---

### Post by lidex on 2010-04-25
> **RationalGaze said:**
> Hello!

I have the same problem. I've tried all solutions posted in this thread, and none of them works :confused:. 
I have a Toshiba A200 with a ALC861VD sound card and running ubuntu 10.04. Currently i have 1.0.22 version of ALSA (tried also with 1.0.23, with no success..). Sound works on speakers, but plugging the headphones in has no effect. Also manually changing the output in sound preferences to a"nalog headphones" doesn't help. It only mutes the speakers..

It worked in 9.10. But it is strange, three days ago i installed 10.04, saw that the sound wasn't working, and again went back to 9.10. On that second 9.10 install i had the same problem! But about 6 months ago, on my first 9.10 install, sound worked out of the box. This is really bothering me...

Any suggestions?

Thanks.

Try this. Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=lenovo  
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels.
Go to "System>Preferences>Sound" and make sure the correct soundcard is default

---

### Post by RationalGaze on 2010-04-26
I have already inserted lenovo, hp, 3stack and none of them works. The wierd thing is, that i get the headphones channel in alsamixer, but cant change the level. 

In preferences -> sound I only have this one card. So it can't be that.

I also tried ALSA drivers 1.0.20, 1.0.21, 1.0.22 and 1.0.23. As i said, it worked on the prevoius install of 9.10 but i don't know which version of ALSA i had. Couple of days ago, i reinstalled 9.10, and found this bug again with ALSA 1.0.20... When i tried to install 1.0.14 (and 15 and 16) it won't install beacuse of extra_cflags. Could this be somehow overriden, so i can try some pre-1.0.20 versions?

Thanks

EDIT: Got sound through both (Headphones & Speakers) simultaneously.
EDIT 2: Solved. 1.0.23 + model = lenovo. Works like a charm :)

---

