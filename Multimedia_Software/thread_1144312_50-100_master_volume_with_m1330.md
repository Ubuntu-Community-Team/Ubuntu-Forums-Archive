---
title: "50-100 master volume with m1330"
date: 2009-04-30
forum: Multimedia Software
---

### Post by jimsleeps on 2009-04-30
My master volume only has any sound from about the 50 to 100 percent range.  So when I adjust the volume I have to start about 60 percent to hear anything.  Then it seems extremely sensitive between 80-100.  So with my keyboard volume button it is very much like having only three settings for volume: loud, medium, soft.
I have a Dell xps m1330 dual boot with Jaunty/Vista (Vista does not have this problem).  I upgraded recently from Intrepid but I had this problem in Intrepid as well.  All of my mixer options in the volume control are set to 100%.


I tried editing the volume_step in the gconf-editor which made each button click from my laptop jump in smaller increments but did not fix the range issue.  Described here:
[[SOLVED] XPS m1330 Volume Buttons too sensitive...]("http://ubuntuforums.org/showthread.php?t=1004757")

This may have been the same problem but none of the solutions have worked for me:
[Sound volume of M1330 is too small?]("http://ubuntuforums.org/showthread.php?t=620992")

I tried adding a line to my etc/modprobe.d/alsa-base.conf to no effect as described here:
[Very low volume sound]("http://ubuntuforums.org/showthread.php?t=373287")

I followed instructions here to setup pulseaudio to no effect:
[Jaunty 9.04 Sound Solutions]("http://ubuntuforums.org/showthread.php?t=1130384")

Any help would be much appreciated!  This is excruciating!

---

### Post by jimsleeps on 2009-05-02
Any advice? (bump)

---

### Post by Gustavo Narea on 2009-05-04
(*bump*)

I have the exact same problem and I haven't found a solution yet. :(

---

