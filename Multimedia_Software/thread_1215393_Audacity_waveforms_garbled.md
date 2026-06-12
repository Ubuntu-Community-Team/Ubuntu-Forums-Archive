---
title: "Audacity waveforms garbled"
date: 2009-07-17
forum: Multimedia Software
---

### Post by Colin@oxford on 2009-07-17
On a new installation of Jaunty I find that the waveform in Audacity (and also on Gnome CD master) is unreadable.  It has horizontal white bars in it and clicking on the waveform causes that damaged bits to move around randomly.  I attach a picture of the offending waveform, in case it helps.

Anyone any ideas where I should be looking for the cause of this fault?

---

### Post by igorzwx on 2009-07-17
Hi!
this is very interesting for me.
We can discuss this on Audacity forum.
They patched Audacity, you know.
[audacity 1.3.8 and pulseaudio]("http://n2.nabble.com/audacity-1.3.8-and-pulseaudio-tp3266457p3266457.html")  									by 									Benjamin Drung 								
[http://n2.nabble.com/audacity-1.3.8-and-pulseaudio-tp3266457p3266457.html](http://n2.nabble.com/audacity-1.3.8-and-pulseaudio-tp3266457p3266457.html)

It might be pulse.
I have now Ubuntu 9.04 without Pulse and ALSA.
I have not problems anymore.
OSS4 works well.

You can install a second Ubuntu in dual boot and see the difference.

---

### Post by Colin@oxford on 2009-07-17
I am not sure I understand.  The sound comes out OK, it is just the visual representation that is bizarre.  Therefore I cannot see how the sound system can make a difference.

---

### Post by igorzwx on 2009-07-17
this is even more interesting.
It might be the same evil.
Too much CPU load.
Believe me, the only way to diagnose the problem
is to have a second Ubuntu on the same box.

[Howto: OSS4 with Ubuntu Lite (Beta, netboot)]("http://www.4front-tech.com/forum/viewtopic.php?t=3237")
[http://www.4front-tech.com/forum/viewtopic.php?t=3237](http://www.4front-tech.com/forum/viewtopic.php?t=3237)

---

### Post by Colin@oxford on 2009-07-17
Today the update manager grabbed a new set "pulse" libraries, so I assume that this is that patch you were talking about.

I have two copies of Jaunty on this box, one is fully up-to-date and the other is a fresh install from CD with Audacity added.  Both display the same problem.  I also have PuppyLinux (Gallibox which comes with Audacity) and this displays my waveforms perfectly.

There is definitely not too much CPU load since the only thing running is Audacity!

---

### Post by igorzwx on 2009-07-17
Puppy may not have Pulse inside.
Do you mean no problems with Puppy?

---

### Post by igorzwx on 2009-07-17
Try:

sudo killall pulseaudio

or something like this.

then deinstall pulse and reboot

You may not have playback in Audacity,
but pictures of waves may become nice

---

### Post by monraaf on 2009-07-17
> **Colin@oxford said:**
> On a new installation of Jaunty I find that the waveform in Audacity (and also on Gnome CD master) is unreadable.  It has horizontal white bars in it and clicking on the waveform causes that damaged bits to move around randomly.  I attach a picture of the offending waveform, in case it helps.

Anyone any ideas where I should be looking for the cause of this fault?

What graphics card do you have? If it's an ATI and you are using the open source drivers, then your problem is probably related to this bug.

[http://bugs.freedesktop.org/show_bug.cgi?id=21561](http://bugs.freedesktop.org/show_bug.cgi?id=21561)

---

### Post by igorzwx on 2009-07-17
The box, perhaps, is not very new.
That is why Puppy.
If the complete removal of Pulse does not help,
it might be a driver, or else.

---

### Post by Colin@oxford on 2009-07-18
I think monraf has it.  The image in that description looks very like mine.  I think I probably have the same graphics chip (how do I confirm this?).  I recall a little window popped up briefly at some point that suggested (I think) getting non-open-source software for the graphics, but it disappeared again.  Any ideas how I get such drivers? 

To answer igorzwx, this is a very new machine - replacing a year-old one that kept failing.  Audacity worked OK on the old machine, but not on the new one.  I thought the graphics chips were the same, but maybe not.

---

