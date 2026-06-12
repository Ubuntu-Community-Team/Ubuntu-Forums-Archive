---
title: "Video freezes during playback (latest 9.04)"
date: 2009-07-12
forum: Mythbuntu
---

### Post by brianko on 2009-07-12
I've spent hours on this one, have tried many things, but no success.  This is my setup:

Asus M2N-E mobo, AMD Athlon 64 X2 4200+ dual core, 2G RAM 
PVR-350
Latest 9.04 Mythbuntu install

Everything seems to work:  Recording, live TV, etc.  The only thing that fails to work is recording playback:  After a few minutes and usually associated with rew/ff/pause actions, the video simply freezes.  I've found that I can recover by HUPing the X server (I can still SSH into the box). Here's a sampling of error output from mythfrontend.log:

2009-07-12 14:53:34.695 IVD Error: Fetching frames played from decoder
                        eno: Input/output error (5)
2009-07-12 14:53:34.696 IVTV rawframes decreased! Did the decoder reset?
<repeats until X server is HUPed>
2009-07-12 14:54:19.100 WriteAudio: buffer underrun
...
2009-07-12 14:56:49.799 IVD Error: Fetching frames played from decoder
                        eno: Input/output error (5)
2009-07-12 14:56:50.803 IVD Error: Fetching frames played from decoder
                        eno: Input/output error (5)
2009-07-12 14:56:56.095 IVD Error: Fetching frames played from decoder
                        eno: Input/output error (5)
2009-07-12 14:56:56.095 IVTV framelist is empty!
2009-07-12 14:56:56.108 TV: Attempting to change from WatchingPreRecorded to None
2009-07-12 14:56:56.160 DPMS Reactivated.
2009-07-12 14:56:56.160 DPMS Deactivated 

Any suggestions other than the hundreds I've already tried that have been posted elsewhere?

BTW, this hardware setup was working fine under an earlier Mythbuntu release, but a hard drive crash required a complete reinstall.  So I'm fairly certain the hardware side of things is sound.

---

### Post by brianko on 2009-07-17
bump...

Anyone?

---

### Post by brianko on 2009-07-20
OK, I've narrowed the problem down:  Playback works fine, but when you try to FF through, the freeze occurs at that point.  Subject changed to reflect this new development.

Still no meaningful error messages though...

---

### Post by brianko on 2009-08-06
Well, after quite a bit of testing, I've determined that there is definitely something buggy about 9.04 on my particular hardware setup.  The system locks up when video playback is paused.  Commercial skip works fine, and playback works fine as well.

I've added my hardware setup to the Functional/Non-functional Hardware thread, with a note about the pause/FF bug.  Be cautious about upgrading to 9.04...

---

### Post by diesel12 on 2009-08-07
What graphics card? this MB doesn't look like it's built-in...

Are you using NVIDIA? XVMC?

---

### Post by kpettersson on 2009-09-15
> **brianko said:**
> 
Asus M2N-E mobo, AMD Athlon 64 X2 4200+ dual core, 2G RAM 
PVR-350
Latest 9.04 Mythbuntu install


Hi! I have a very similar setup: AMD Athlon 64 X3 and PVR-150, Mythbuntu. I'm using the HD3300 integrated graphics and the latest graphics driver from AMD.

I too experience a random freeze/pause during TV-playback. The only error message I've detected so far is complains about not being in the pulse-rt group when playing sound (fixed).

I'm a bit desperate. Everything worked flawlessly before I upgraded.

Sometimes only the sound disappears, but mostly the loss of sound follows with a frozen playback and no response from (USB-driven) keyboard/mouse or remote.

After 5-10 minutes everything comes back to normal.

The problems seems to occur randomly. I've had continuous playback for 4 hours without a problem and once it got stuck after only a few minutes.

---

### Post by brianko on 2010-01-04
Unfortunately, this problem remains unresolved. In addition, sound dropped from all recorded video. Upgrading to 9.10 completely broke the mythtv install. I've thrown in the towel, as mythtv seems to become more problematic as new versions are released, and community support is sorely lacking (no need to berate me on this point; as an open source developer I'm well aware of the hit or miss nature of F/OSS community support). The box has been retired. My solution to the problem is Moxi ([http://www.moxi.com](http://www.moxi.com)). Given the 20+ hours I've worked on this problem, at $40/hour it's time to cut my losses and bail.

---

