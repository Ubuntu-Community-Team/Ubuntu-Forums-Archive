---
title: "[SOLVED] Soo, when I installed Gutsy, I had sound.  Now, I don't.  Huh?"
date: 2007-11-11
forum: Multimedia &amp; Video
---

### Post by inchaos on 2007-11-11
I used the Live CD to install Gutsy on my Dell 1420n laptop.

With the Live CD and for the first day or so after the install, my sound worked wonderfully.

I woke up today and all of the sudden, there's no sound.

Yes, the volume is all the way up, no, it's not muted, yes, everything is all the way up in alsamixer.

I've got Intel HD Audio (HDA Intel), my card is detected, etc. etc. etc.

All I've done is install the usual programs, Exaile, gtkpod, Listen, VLC, and the basic a/v codecs.  I've also installed Wine.  The only thing I can think of is that maybe somehow it's Compiz or something like that.  I'll disable Compiz and reboot to see if that's to blame.  I've installed the backports and followed the guide on the Dell wiki for getting sound in Feisty (they don't offer any help for Gutsy yet).

So, when your card is detected and the volume is up, what else can you do?

---

### Post by negerbarn on 2007-11-12
I have the EXACT same problem!! I just installed Gutsy, then one week later the sound in vlc  and my speakers disapperad... dont get it. My sound works in xmms, not with the speakes but with the sound from the computer. Searching for a solution..

---

### Post by Levander on 2007-11-12
For sound problems in general:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

For HDA Intel sound in specific:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

One of the things in that guide is to try to install the alsa drivers from scratch by compiling themself.  I think that's pretty much the same thing I did by following the instructions in the  post #10 by chinook in this thread:

[http://ubuntuforums.org/showthread.php?t=569082](http://ubuntuforums.org/showthread.php?t=569082)

---

### Post by inchaos on 2007-11-12
Thanks for those links, I'm trying them one by one....

---

### Post by nebbe on 2007-11-12
Y0 dudes,

Same issue here.. Installed Gutsy on an amd64- 
Sound worked perfect.. today, its gone.. completely.

Although, i noticed something inside alsamixer once i compared it to another laptop in my house.

Settings for "Master", "Master M" is gone on the amd64 Gutsy-version..


Have u guys those options still in your alsamixer, or have they vanished?

Ive tried to "sudo apt-get --purge remove alsa-base alsa-oss alsa-utils" and then reinstall them again.. didnt do the trick :(

How do we fix this??

cheers!

---

### Post by inchaos on 2007-11-12
Oh God, what have I done?

Jeeze.  Ok.  

So I recompiled the ALSA driver first and foremost, that didn't do anything.

I'm also noticing a weird configuration in alsamixer that seems out of the ordinary.  It's just listing a bunch of channels I don't have or have never used...but I think you can change those by right clicking your volume control applet and going to sound preferences and then picking the channels you want to control.  Maybe I'm wrong, I can't get into my volume applet right now because.....

I followed the directions here:
[http://ubuntuforums.org/showthread.php?t=569082](http://ubuntuforums.org/showthread.php?t=569082)
Under post #10.
The install was flawless, I was starting to get excited about SOMETHING working...

So I rebooted like it said to do, all of the sudden I have NO sound card detection WHATSOEVER.
I try to open my volume control applet and I get a message that says: No volume control GStreamer plugins and/or devices found.  Under my sound settings for my default Mixer settings I have null where I used to have Sigmatel something or other, AKA my chipset.

So...I removed the module assistant that the post said to install and recompiled ALSA again.
Oh, by the way, I've also lost alsamixer somehow this morning, I'm not sure if the module assistant removed it, cause I sure didn't!

So.  How to fix alsamixer and sound card detection...

The search begins now.

---

### Post by inchaos on 2007-11-12
Oh, I lied.

I was reading incorrectly.

I have alsamixer, but it's not detecting my card.  I get this:

```
~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
```

---

### Post by inchaos on 2007-11-12
Woohoo!  Sound is awesome.

I finally got fed up because my sound card wasn't detected, so I uninstalled/reinstalled everything sound-related.

```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
```

This also removes ubuntu-desktop and gdm, so I did this:

```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop
```

Rebooted, and it works!

Dunno what caused it to get borked up in the first place, but I'm not worrying about it.

---

