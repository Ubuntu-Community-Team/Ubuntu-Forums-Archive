---
title: "Sound randomly disabled"
date: 2007-06-28
forum: Multimedia &amp; Video
---

### Post by Hanj on 2007-06-28
I'm running Ubuntu Studio and I have an M-Audio Audiophile 2496 sound card. My problem is that sometimes when I boot the machine (about 50% of the time, seemingly random), all sound is completely disabled and I have to reboot to make it work again.

It's been like this since I did a fresh install, so it can't be some program I installed. I'd post more info, but I don't really know what to look for, so it'd be really nice if someone could at least give some tips on where to begin.

---

### Post by agent154 on 2007-06-29
Interesting, because I'm also looking for a solution to that exact same thing... Sometimes (likewise about 50% of the time) I turn on the computer and everything loads up except sound support... then when I reboot, it starts up normally... What variables could be causing this, especially when each time you start up the computer, it should be following the same loading processes each time?

---

### Post by Hanj on 2007-06-29
One weird thing I noticed is that when sound *is* working after a reboot, the volume applet in the panel claims that it is muted (which it isn't). It says "Multi: muted" when hovering over it. After a reboot when it does *not* work, however, it doesn't say it's muted. I have no idea what to make of this.

---

### Post by paulg on 2007-06-29
Do you have the envy control panel installed? 

```
sudo aptitude install envy24control
```

Then run the program. Should get you going ;)

Edit: Huggy, this won't help your problem. It's for the envy24 based cards (such as the M-Audio Delta series) only.

---

### Post by Huggy on 2007-06-29
I'm having the exact same problem except I have a sound audigy blaster card that uses emu10k1. This has got to be a bug of some kind. I know I haven't been able to fix it all week which is bad because I'm a sound tech! and I need this for studio recording. My sound board is plugged directly into my computer and i use the computers interfacing. So when i get my computer's sound fixed everything else will work again. Sometimes I'll have to reboot 6 or 7 times to get it to come back on, and sometimes it'll work for 2 or 3 boots strait. I don't get it. Anybody have any ideas?

---

### Post by Hanj on 2007-06-29
Found the problem. Turns out the system was set to automatically detect the default sound card, and for some reason it sometimes found the onboard sound card and sometimes the M-Audio. I switched off autodetection, so hopefully it should work now.

---

### Post by BlueSun on 2007-06-29
Hey all, whenever I have intermittent sound issues, the first place I go is the terminal program [alsamixer]("http://en.wikipedia.org/wiki/Alsamixer").

```
~$ alsamixer
```

For whatever reason, one of the values (usually PCM) will be set to zero, and as soon as I turn it back up, the sound works normally.  I have no idea why this happens, but it usually occurs when I'm running a Flash player in Firefox and simultaneously trying to listen to music with Amarok or watch a movie on Kaffeine.

---

### Post by agent154 on 2007-06-29
> **Hanj said:**
> Found the problem. Turns out the system was set to automatically detect the default sound card, and for some reason it sometimes found the onboard sound card and sometimes the M-Audio. I switched off autodetection, so hopefully it should work now.

How do you do that?

---

### Post by Hanj on 2007-06-30
> How do you do that?Just go to Administration->Sound and change the values.

EDIT: Turns out that only solved the problem partially (I still couldn't get system sounds to work). After googling around a bit I found out this is a known bug which has been around for a while. Workarounds can be found in [this bug report]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/45786").

---

### Post by Hustle Kong on 2007-07-09
> **BlueSun said:**
> Hey all, whenever I have intermittent sound issues, the first place I go is the terminal program [alsamixer]("http://en.wikipedia.org/wiki/Alsamixer").

```
~$ alsamixer
```

For whatever reason, one of the values (usually PCM) will be set to zero, and as soon as I turn it back up, the sound works normally.  I have no idea why this happens, but it usually occurs when I'm running a Flash player in Firefox and simultaneously trying to listen to music with Amarok or watch a movie on Kaffeine.



Nearly a year later, this advice helped me. thanks!!

---

