---
title: "Mysterious Glitchy Audio"
date: 2010-05-16
forum: Multimedia Software
---

### Post by Imashinu on 2010-05-16
So out of the blue my computers audio started to act really odd. Every few seconds in a song or video the sound makes a skip/glitchy noise. I wasn't doing anything at the time and a restart didn't help. No updates where applied, so it just started happening at random. I am running Lucid and I have been using it without a problem for since the beta. I have no idea what could have happened, any ideas?

---

### Post by Imashinu on 2010-05-16
Anyone have an idea on this one?

---

### Post by lidex on 2010-05-16
Something like this?
[http://rightfootin.blogspot.com/2009/05/fixing-pulseaudio-stutters-pauses.html]("http://rightfootin.blogspot.com/2009/05/fixing-pulseaudio-stutters-pauses.html")

---

### Post by Imashinu on 2010-05-16
That sounds like my problem but the solution completely broke my sound. 

But now I'm also having more issues. Now when I play flash sound on all other programs lose sound. When I play sound through other programs, flash sound stops working.

And I still have the shuttering problem ontop of that :-/.

---

### Post by lidex on 2010-05-16
Have a look here:[http://ubuntuforums.org/showthread.php?t=1455816]("http://ubuntuforums.org/showthread.php?t=1455816")
And/or here:
[http://ubuntuforums.org/showthread.php?t=1412153]("http://ubuntuforums.org/showthread.php?t=1412153")

---

### Post by Imashinu on 2010-05-16
Thank you :), that fixed the issue with flash and other programs, but I still have this stutter problem :(.

---

### Post by lidex on 2010-05-17
Some have reported there may be a bug causing that.

See 'Appendix B' here and I would suggest working through 'Part A':
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

Now this. Update your kernel:
```
sudo apt-get update
sudo apt-get upgrade
```
Now reboot so we can work with the latest kernel.
Install alsa backports:
```
sudo apt-get install linux-backports-modules-alsa-lucid-generic
``` Reboot again.

---

### Post by Imashinu on 2010-05-18
Well, I tried what you said, and the stuttering is still there with no improvement. I feel like a fresh install is all that will fix this :(

---

