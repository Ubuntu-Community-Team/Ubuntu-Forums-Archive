---
title: "HOWTO:  Get Audio working on a linux Vmware host running esd or Pulseaudio, or ALSA"
date: 2007-10-09
forum: Multimedia &amp; Video
---

### Post by Jazzyman on 2007-10-09
Hello all,

I had this problem for a while, and I've seen tons of posts on various forums floating around the net on this issue.

The problem arises when you boot up a VM guest that tries to access /dev/dsp.  VMware denies you access because the OSS device is already in use by the Pulseaudio daemon or ALSA.

There are several solutions that include using an esd wrapper and all sorts of fancy stuff like that, but here is a simple solution that worked for me, I'm running Ubuntu 7.04 and VMWare workstation 6.  (this solution may only apply for VMWare 6+)

[INDENT][LIST=1]
[*]Open your guest's settings
[*]Change the physical sound adapter from /dev/dsp or Auto detect to /dev/audio
[/LIST][/INDENT]

That's it!  Amazingly after hours of searching, that's what did it for me.  I hope this works for you too.

---

### Post by K.Mandla on 2007-10-24
Moved to Multimedia. :)

---

### Post by confy on 2008-01-27
this is useful but there is still problem playing sound simultaneously.. 

there is also solution provided by xp_noob & others: 
[http://ubuntuforums.org/showthread.php?t=331175](http://ubuntuforums.org/showthread.php?t=331175)

which is somehow more advanced....

---

### Post by Kent_Geek on 2008-03-27
I'm running Gutsy (x64), and installed Pulse Audio.  When I changed the sound adapter settings on my VMs to use /dev/dsp1, simultaneous audio (with no skipping or ugliness so far) was the result.  

This is on the latest version of VMWare Workstation, so your mileage may vary.

---

### Post by nightfever on 2008-04-29
> Change the physical sound adapter from /dev/dsp or Auto detect to /dev/audio
done that and it says device busy

---

### Post by fuelrod on 2008-05-05
> **Kent_Geek said:**
> settings on my VMs to use /dev/dsp1

Maybe its because i'm running a 32bit system but this device does not appear to exist.

---

