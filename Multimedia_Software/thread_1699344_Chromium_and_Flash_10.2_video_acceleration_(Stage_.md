---
title: "Chromium and Flash 10.2 video acceleration (Stage Video)"
date: 2011-03-03
forum: Multimedia Software
---

### Post by thecapsaicinkid on 2011-03-03
Ubuntu 10.10 64bit
Chromium and Flash 10.2 from the repos
Nvidia GT210
VDPAU working as expected

Right clicking on YouTube videos which supposedly have Stage Video acceleration enabled (link below) and viewing video info shows 'Software Rendering' and cpu is still around 60%.

[http://www.youtube.com/watch?v=Ou6_MkIvKOo&feature=player_embedded](http://www.youtube.com/watch?v=Ou6_MkIvKOo&feature=player_embedded)

Has anyone got this working? 60% cpu hints that it's not working.

Curiously, the Big Buck Bunny test video on Adobe's site shows Stage Video = true (cpu still around 60%) yet the same video on YouTube maxes the cpu.

---

### Post by thecapsaicinkid on 2011-03-05
Any ideas?

---

### Post by Yellow Pasque on 2011-03-05
Stage video doesn't work with 64-bit Flash. I'm not sure if it works using the 32-bit Flash and nspluginwrapper.

---

### Post by thecapsaicinkid on 2011-03-08
Forgot to mention I was using the 32bit version with nspluginwrapper.

Not sure if this is an issue with Chromium, the flash binary or some other problem caused with by using a 32bit binary on a 64bit system.

---

### Post by kerry_s on 2011-03-08
> **thecapsaicinkid said:**
> Forgot to mention I was using the 32bit version with nspluginwrapper.

Not sure if this is an issue with Chromium, the flash binary or some other problem caused with by using a 32bit binary on a 64bit system.

32 does the same thing.
go into about:flags & enable the gpu accel stuff, just in case.

---

### Post by thecapsaicinkid on 2011-04-03
Flash just been updated and it STILL doesn't work.

---

### Post by thecapsaicinkid on 2011-05-01
Still no hardware acceleration.

---

### Post by thecapsaicinkid on 2011-05-29
Does anyone have VDPAU accelerated Flash working with Chromium?? Yet more Flash binary updates and it STILL does't work.

---

### Post by Yellow Pasque on 2011-05-29
I'm assuming you have the 32-bit version of libvdpau since you posted in this thread: [http://ubuntuforums.org/showthread.php?t=1636333](http://ubuntuforums.org/showthread.php?t=1636333)
Is that correct?

---

### Post by thecapsaicinkid on 2011-05-29
I'm guessing it's 64bit. There's no mention of 32bit.

0.4.1-2ubuntu1

---

### Post by Yellow Pasque on 2011-05-29
Follow the instructions in that thread to get the 32-bit libvdpau using getlibs.

---

### Post by thecapsaicinkid on 2011-05-29
That worked, thankyou so much!


I'm not sure I understand how getlibs works. It doesn't add a visible package to the package system, in Synaptic I still see just the original 64bit libvdpau1 package. I'm guessing I have both 32/64bit now and native 64bit apps like mplayer will still use the 64bit vdpau?

EDIT: Browser became unresponsive after a while, will reboot and try again.


Thanks again.

---

### Post by Yellow Pasque on 2011-05-29
getlibs just extracts the shared libraries out of the package and places them in /usr/lib32. That violates Debian packaging policy and you might need to do it again if you choose to upgrade the system. It's not the cleanest solution for the 64-bit user (that would be a chroot), but I haven't seen complaints about getlibs borking peoples' systems either (even when we had a 64-bit subforum and a lot more need for getlibs).

---

