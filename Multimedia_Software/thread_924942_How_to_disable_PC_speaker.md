---
title: "How to disable PC speaker?"
date: 2008-09-20
forum: Multimedia Software
---

### Post by stromdal on 2008-09-20
I have a MythBuntu box connected to my TV and amp/speakers for watching movies from HDD, DVD etc. The sound behaves somewhat strange, though. Even though I've connected a cord to the sound output jack I still get sound from the PC speaker (the sound from the movie). What's even weirder is that if I play a DVD the sound control has no effect on the sound level; the DVD sound is outputted though the PC speaker at max level no matter what I do.

I've tried 
```
sudo rmmod pcspkr
```
and
```
sudo modprobe -r pcspkr
```
with no effect.

Anyone has any idea on how to solve this problem, or should I just physically yank out the speakr from the box?

---

### Post by Rui Pais on 2008-09-22
> **stromdal said:**
> I have a MythBuntu box connected to my TV and amp/speakers for watching movies from HDD, DVD etc. The sound behaves somewhat strange, though. Even though I've connected a cord to the sound output jack I still get sound from the PC speaker (the sound from the movie). What's even weirder is that if I play a DVD the sound control has no effect on the sound level; the DVD sound is outputted though the PC speaker at max level no matter what I do.

I've tried 
```
sudo rmmod pcspkr
```
and
```
sudo modprobe -r pcspkr
```
with no effect.

Anyone has any idea on how to solve this problem, or should I just physically yank out the speakr from the box?


Hi stromdal, sometimes modules can't be unloaded/removed after they been loaded or in use.

Try edit edit your file:
/etc/modprobe.d/blacklist
and add:
```
blacklist pcspkr
```
then reboot. It should prevent the automatic load of the module.

hth

---

### Post by misuchiru03 on 2009-02-03
I had this problem after switching to Ubuntu.  Tried hard to search threads, and they all said the same thing.  If blacklist pcspkr doesn't work and, even when you reboot, you still hear the pc speaker, try this:

Open Volume Control
(it should open under your default audio)

You should find Master on the left, right next to that you should see Master Mono; if you do not see Master Mono, click Preferences

In Preferences, find Master Mono, and check it, then click close.

It should appear to the right of Master.
--Take it from here and mute it, or lower it to desired volume.

This should take care of the PC speaker.  I was messing around when I discovered that.  I basically added all the little switches and controls and messed with it until I did it, and I actually had to do a reinstall (the cd I used didn't work fully, and the OS wasn't fully installed.  Second time worked perfectly though), and I couldn't remember how I did it.  I hope this helps anyone looking for the answer

---

