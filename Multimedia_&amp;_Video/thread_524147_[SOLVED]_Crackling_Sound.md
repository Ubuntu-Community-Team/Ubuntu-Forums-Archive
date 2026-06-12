---
title: "[SOLVED] Crackling Sound"
date: 2007-08-12
forum: Multimedia &amp; Video
---

### Post by jusmurph on 2007-08-12
At low volume (and i have adjusted PCM levels to >50%) and the problem continues.

I know i never had this before i reinstalled.

I have and Audigy 2 PCI sound card which is set as default and using the ALSA mixer.

Do i need to update ALSA? This is really weird considering i have installed Ubuntu 4 times and this is the first time it has a appeared?

---

### Post by Onay on 2007-08-12
Open up the volume control properties and check all of the options and have them all marked, as well as all of the switches.

Enable switches such as depth, tone, and anything else besides the Audigy out jack. Then mess a bit with the volume settings. Tone is a big one, because it will let you change the surround sound, treble, bass, etc. Also turn up the main system volume to 100% and turn down your speakers a bit.

It won't sound like Windows Media Player 11 with SRS and WOW, but it still is a HUGE improvement to the stock setup.

---

### Post by PhenixRising on 2007-08-17
> **jusmurph said:**
> At low volume (and i have adjusted PCM levels to >50%) and the problem continues.

I know i never had this before i reinstalled.

I have and Audigy 2 PCI sound card which is set as default and using the ALSA mixer.

Do i need to update ALSA? This is really weird considering i have installed Ubuntu 4 times and this is the first time it has a appeared?

I was having the same problem.  I still can only get my fronts to work but I stopped it from crackling.  Open up alsa but play music while you are messing around with the sound.  The default settings were just too high for my speakers.  I moved it down until the music stopped crackling.  Give it a try.

---

### Post by jusmurph on 2007-08-19
> **PhenixRising said:**
> I was having the same problem.  I still can only get my fronts to work but I stopped it from crackling.  Open up alsa but play music while you are messing around with the sound.  The default settings were just too high for my speakers.  I moved it down until the music stopped crackling.  Give it a try.

I have done that and it just does not work...

Its kind of depressing... I did a re install and its fine... then today it just starts hissing, even at low volumes.

---

### Post by Gremlinzzz on 2007-08-19
Seems like a good site for help in fixing sound
[http://www.linuxjournal.com/node/1000262](http://www.linuxjournal.com/node/1000262)

---

### Post by jusmurph on 2007-08-19
> **Gremlinzzz said:**
> Seems like a good site for help in fixing sound
[http://www.linuxjournal.com/node/1000262](http://www.linuxjournal.com/node/1000262)

Cheers.

---

### Post by jusmurph on 2007-09-01
SOLVED

From Lord Raiden's Sound Guiode noted in my sig!


> [U][B][SIZE=3]
Getting the ALSA drivers from a *fresh* kernel[/SIZE][/B][/U][SIZE=2]

Sometimes, sound might be configured correctly, but for some reason or another (tinkering) it stops working. One way to go back to the old setup is to reinstall **Ubuntu**. However, this step is actually quite unnecessary since you are reinstalling everything because of one thing.[/SIZE][SIZE=2]

A faster way, is to just remove the problematic packages and reinstall them cleanly.[/SIZE] [SIZE=2]

(1) Remove these packages```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils 
``` [/SIZE][SIZE=2]
(2) Reinstall those same packages[/SIZE][SIZE=2]
```
sudo apt-get install linux-sound-base alsa-base alsa-utils 
``` [/SIZE]
[LIST]
[*][LEFT][LEFT] [SIZE=2]**VERY IMPORTANT NOTE: **Ubuntu (GNOME) users have reported that packages 'gdm' and 'ubuntu-desktop' are removed after removing the linux-sound-base packages. If this happens, then do the following[/SIZE]
[SIZE=2]```
sudo apt-get install gdm ubuntu-desktop
``` [/SIZE]
[SIZE=2](3) Reboot[/SIZE][/LEFT]
[/LEFT]
[*][LEFT][LEFT] [SIZE=2]**VERY IMPORTANT NOTE: **Xubuntu (XFCE) users have reported that packages 'gdm' and 'xubuntu-desktop' are removed after removing the [/SIZE][SIZE=2]linux-sound-base[/SIZE][SIZE=2] packages. If this happens, then do the following[/SIZE]
[SIZE=2]```
sudo apt-get install gdm xubuntu-desktop
``` [/SIZE]
[SIZE=2](3) Reboot[/SIZE]
[SIZE=2]Now you may ask "I already had the packages, so why did I go through the trouble of removing them, then installing them". The answer lies in the --purge option which removes all the extra information that accumulated from tinkering and upgrading. After doing a purge then install, the packages are unpackaged as if it they are brand new.[/SIZE]

---

