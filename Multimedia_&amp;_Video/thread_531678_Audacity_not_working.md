---
title: "Audacity not working"
date: 2007-08-21
forum: Multimedia &amp; Video
---

### Post by madsmeg on 2007-08-21
```

Error while opening sound device. Please check the input device settings and project sample rate.

```

This is the message i get when trying to record i have changed options and lowered rates yada yada.

Ok im lost and im tired, i have just downloaded and installed the latest drivers for my motherboard hoping it would resolve the issue, but nothing, if anyone has any idea's i will be checking the forum in a few hours after sleep.

Thanks in advance.

Teh smeg

P.S. i didnt know where else to post this, if someone could redirect me i would be most happy

---

### Post by Seti on 2007-08-21
What is your soundcard and how does it show up in /dev?

Under the playback and Recording sections of the Audio I/O tab in Preferences, my audigy soundcard shows up as:

Device: OSS: /dev/dsp

for both Playback and Recording.

Bottom line, find out what kind of soundcard you have and how linux names it under /dev/

good luck

---

### Post by Arrdee on 2007-08-22
I just installed Audacity and I'm getting a similar problem - I can't play any files. In the preferences, under Playback, it doesn' t have any options in the pulldown menu. I'm pretty stumped...

---

### Post by madsmeg on 2007-08-22
i dont have a soundcard, its onboard sound (nForce 4) useing realtek drivers will try your solution when i get home and let you know how i got on.
Thanks

Teh Smeg

---

### Post by madsmeg on 2007-08-22
i tried recording under OSS: dev/dsp, when i have no lead plugged in, it records, well nothing (obviously :P) as soon as i plug a lead in, i get the same message, unsure as to how to go about sorting this out :(

Teh Smeg

---

### Post by shahrc on 2007-08-23
Got the same problem here,

[IMG]http://img477.imageshack.us/img477/1664/screenshoterrorinitialiuw6.png[/IMG]

[IMG]http://img411.imageshack.us/img411/205/screenshoterror2ys0.png[/IMG]

All other functions of the program works accept for recording and playing the files. For the time being I'm using Sound Recorder to record sound and edit with Audacity.

I not an expert reading my devie hardware but here is my snapshot of device menager if anyone could help me.

[IMG]http://img502.imageshack.us/img502/863/screenshotdevicemanagertx0.png[/IMG]

---

### Post by madsmeg on 2007-08-23
Well at least I'm not on my own. Still have had no success as of yet.

Teh Smeg

---

### Post by shahrc on 2007-08-26
Is there any configuration files need to be edited so as Audacity could point to the correct devices for playback or recording..

---

### Post by Amazona aestiva on 2007-08-26
See the link in my signature.
Audacity is at the bottom of that page.

---

### Post by wormser on 2007-08-29
I am receiving the same error.  There is a [bug]("https://bugs.launchpad.net/feisty-backports/+bug/107207") filed for this error.  Apparently it has been resolved in Gusty Gibbon and a request has been put in for Feisty Fawn.  My guess is that it has not be fixed in Feisty yet.

> 

Thank you for taking the time to report this bug and helping to make Ubuntu better. However, I am closing it because the bug has been fixed in the latest development version of Ubuntu - the Gutsy Gibbon.

A backport request has been made to fix this in feisty.


---

### Post by vanadium on 2007-08-29
The Audacity that comes with the repositories indeed does not work. I have been able to get a working Audacity (be it the 1.30 version) installing a compiled version from this blog: [http://funky.stadtkapelle-heidenreichstein.org/2007/04/17/audacity-132-beta-for-ubuntu-edgy-eft/](http://funky.stadtkapelle-heidenreichstein.org/2007/04/17/audacity-132-beta-for-ubuntu-edgy-eft/)

It is a *.deb for edgy, but I installed it without error on Feisty. Starting audacity from the command line learned that "audacity: error while loading shared libraries: libFLAC++.so.5: cannot open shared object file: No such file or directory". Using synaptic, I installed libflac++5c2, after which Audacity would run well, with a tight Gnome look as a bonus.

---

