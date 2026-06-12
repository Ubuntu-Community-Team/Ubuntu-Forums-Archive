---
title: "Upgraded to Karmic, lost the ability to control volume"
date: 2009-11-04
forum: Multimedia Software
---

### Post by IAmNoodle on 2009-11-04
Hi all. Yet another sound problem.

Since upgrading to 9.10, my sound most definitely works, but I'll be damned if I can control the volume of it! Fortunately, it's at a workable, if quiet level, but it will only ever stay at that volume. No amount of changing the slider or muting/unmuting will make any difference.

Previously on Jaunty, preferences from the sound icon would take me to a menu where I could select from various mixers and buttons. A few of them would be able to control my volume.

On Karmic, clicking preferences takes me to the general sound options, where I can't really do anything at all to control anything. Am I missing something, or is this an early bug in the system?

Cheers

---

### Post by kag9000 on 2009-11-04
Hi,

Type alsamixer in a console. Use the arrow keys to move around and adjust volumes.

Edit. Also check your settings in system>preferences>sound. Particularly the Connector box in the Output tab.

---

### Post by michy99 on 2009-11-04
Look at this thread and try Part A. This fixed my sound problems.

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by IAmNoodle on 2009-11-04
Thanks for the link, but nothing on that page made any difference really. Just added to my applications menu. 

The output in the sounds looks a little something like the attatchment

---

### Post by marcobbi on 2009-11-04
same here. I follow the michy99 link but it didn't solve for me.

In addition, if i Type:

```
marcobbi@marco:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory
marcobbi@marco:~$ 

```

My Volume is fu**ing high! :-)

---

### Post by Kushkah on 2009-11-04
> **marcobbi said:**
> same here. I follow the michy99 link but it didn't solve for me.

In addition, if i Type:

```
marcobbi@marco:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory
marcobbi@marco:~$ 

```

My Volume is fu**ing high! :-)

Make sure your user is in both the plugdev and audio groups ( System > Administration > Users and Groups ), and check out this thread: [http://ubuntuforums.org/showthread.php?t=1309427](http://ubuntuforums.org/showthread.php?t=1309427)

---

### Post by marcobbi on 2009-11-04
Thank You!:P

---

### Post by IAmNoodle on 2009-11-05
No luck for me thus far

---

### Post by IAmNoodle on 2009-11-09
Still nothing. Is it significant in any way that nothing appears in the list under Hardware in sound preferences?

---

### Post by IAmNoodle on 2009-11-18
Quick update. I still don't know what the problem was, but re-installing Karmic gave me back control of my volume. 

What puzzles me is that before (the version of 9.10 I upgraded to from 9.04), alsa was supposedly installed, according to Synaptic, but I couldn't load up alsamixer from either the terminal nor via the applications menu. I also had no hardware listed under the hardware tab in the sound preferences, there was nothing listed under the input tab, and when something did appear in the Hardware tab, I couldn't get any sound at all. 

On this fresh install, everything works fine.

I guess that provides little info as to what the problem actually was, and I'm not really knowledgeable enough to give any technical insight into it either, only describe the symptoms, in the slim chance that someone can identify what the problem was and provide an answer to anyone else who may have the same problem.

Either way, a fresh install did the trick for me

---

