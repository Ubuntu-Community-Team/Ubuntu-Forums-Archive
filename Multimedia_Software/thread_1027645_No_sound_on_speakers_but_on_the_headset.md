---
title: "No sound on speakers but on the headset"
date: 2009-01-01
forum: Multimedia Software
---

### Post by tatsuya42 on 2009-01-01
Hello everyone,

As im new in the community of Linux Ubuntu, I have some trouble.

My first big problem is about the sound.

I Have sound on my headset (mini- jack coonection)
but not on the speakers.
Also the speakers work well on Windows.

I'm using a laptop HP with HDA ATI SB sound card
and been looking to fix this for a while now.
Also, I'm French , I've tried to explain this on the french ubuntu forum but it's seem like no one found the answer at this problem maybe someone here will find it out.

Thanx for reading me. :)

---

### Post by Stochastic on 2009-01-01
Moved to Multimedia & Video.

---

### Post by 2hot6ft2 on 2009-01-01
> **tatsuya42 said:**
> Hello everyone,

As im new in the community of Linux Ubuntu, I have some trouble.

My first big problem is about the sound.

I Have sound on my headset (mini- jack coonection)
but not on the speakers.
Also the speakers work well on Windows.

I'm using a laptop HP with HDA ATI SB sound card
and been looking to fix this for a while now.
Also, I'm French , I've tried to explain this on the french ubuntu forum but it's seem like no one found the answer at this problem maybe someone here will find it out.

Thanx for reading me. :)
Have you tried right clicking on the volume applet in the top right task bar, selecting Open Volume Control, make sure the speakers aren't turned off there.
Click on File > Change Device
Or Edit > Preferences and make sure it's set there.
Or the Switches Tab and marking the Duplicate Front box.

---

### Post by tatsuya42 on 2009-01-01
yeah, it's all turned on...

I tried many thing but it seems like Ubuntu doesn't find my Speakers...

Any idea?

---

### Post by 2hot6ft2 on 2009-01-01
Well at least you know your sound works it's just going out the wrong place so it's in the setting somewhere. And there are so many.

Do you have Applications>Sound & Video>Gnome ALSA Mixer?

If not put this in a terminal to get it
Applications>Accessories>Terminal
```
sudo apt-get install gnome-alsamixer
```

---

### Post by tatsuya42 on 2009-01-01
I have it :/
also tried to re instal it like many topic told ....

another idea ? :confused:

---

### Post by 2hot6ft2 on 2009-01-01
Other things to check
System>Preferences>Sound
try auto, ALSA and Pulse Audio and use the test buttons.

If still no luck.

Applications>Sound & Video>PulseAudio Device Chooser
If you don't have it use this to get it
Applications>Accessories>Terminal
```
sudo apt-get install padevchooser paman
```
That will also get you
Applications>Sound & Video>PulseAudio Manager

---

### Post by 2hot6ft2 on 2009-01-01
If after checking all these and still nothing I'll have to send you to check some other threads for an answer.
[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

PulseAudio is tightly integrated in Intrepid 8.10 and you're not the only one to have issues with it so I'll offer some other links that may help.

These are about no sound maybe one will help.
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

Here are a few other options to choose from from fixing pulse to disabling it and using asla, or replacing pulse with esound.

First fixing pulse
[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

Disabling pulse and using alsa (Before deciding to remove pulse you should read the warning here as to what the result could be).
[http://forumubuntusoftware.info/viewtopic.php?f=46&t=2179&start=0&st=0&sk=t&sd=a](http://forumubuntusoftware.info/viewtopic.php?f=46&t=2179&start=0&st=0&sk=t&sd=a)
and another one going the same route here
[http://ubuntuforums.org/showthread.php?p=6370902#post6370902](http://ubuntuforums.org/showthread.php?p=6370902#post6370902)

Replacing pulse with esound
[http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)
A short version here. I suspect it will be modified.
[http://ubuntuextreme.blogspot.com/2008/12/how-to-fix-audio-in-intrepid-ibex.html](http://ubuntuextreme.blogspot.com/2008/12/how-to-fix-audio-in-intrepid-ibex.html)

There are more but this gives you some alternatives that are being used.

---

### Post by tatsuya42 on 2009-01-01
Well, I think I found,

I don't have the tab pour Speakers on Alsa mixer...  any idea how I can make it apear in???

( it isn't in available in Preferences..)

---

### Post by jsteinaa on 2009-01-04
I have the exact same problem. Plenty of sound in the headset, but no sound from the speakers - and no pc speakers in the mixer.

Found a solution?

---

### Post by tatsuya42 on 2009-01-04
no solution found at the moment ...

---

### Post by tatsuya42 on 2009-01-05
maybe this will help :

[http://img266.imageshack.us/my.php?image=screenshot2vd9.png](http://img266.imageshack.us/my.php?image=screenshot2vd9.png)

Thanx for help!

---

### Post by IQRules on 2009-01-05
I have similar issue on Intel ICH5 device, snd-intel8x0 on 64-bit HP xw6200.
Somehow 32bit liveCD no problem. What is the sound device here, lspci -v and aplay -l and aplay -L.

---

### Post by IQRules on 2009-01-05
Hi, tatsuya42,

The driver module is snd-hda-intel.

[http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel](http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel)

What HP model you have here? HP Compaq business more detail is needed.

---

### Post by michelle02x on 2009-01-05
My cousin had a similar problem and I think he was able to find a solution. I'll try to ask him what he did and post back here asap.

---

### Post by fred_kard on 2009-01-05
Have you try this```
alsamixer -D  
```

---

### Post by IQRules on 2009-01-06
Found this, [http://ubuntuforums.org/showthread.php?t=198305](http://ubuntuforums.org/showthread.php?t=198305)

Dell Dimension ICH5 no sound solved

---

### Post by IQRules on 2009-01-07
I solved my problem on ICH5 with gnome-alsamixer, saw PCM was in mute mode.
Changed PCM to un-mute. What a suprise.

---

### Post by fathead_gti on 2009-01-11
tatsuya42, I have exactly the same problem mate.

I'm using an HP Compaq 6735s Laptop using the same audio hardware. I have had no joy fixing it as of yet, plus I have no idea what i'm doing because I started using Ubuntu yesterday :p

---

### Post by IQRules on 2009-01-12
Did you try gnome-alsamixer? Open a xterm program and run it.

---

### Post by fathead_gti on 2009-01-12
Just fixed it for my laptop.

As I said before I had the same problem and a similar laptop and I gave this a try:

[http://ubuntuforums.org/showthread.php?t=806620]("http://ubuntuforums.org/showthread.php?t=806620")

Worked a charm!

---

