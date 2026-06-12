---
title: "MythTV=choppy, VLC=smooth"
date: 2008-04-12
forum: Mythbuntu
---

### Post by jweida on 2008-04-12
Hi, 
I did a fresh install of Mythbuntu 7.10, I have run through all the auto-updates afterward.  MythTV and Mythbuntu rock.  Cheers to the devs, and thanks for all your work.

Hardware
CPU: P4 1.3 GHz
RAM:640 MB RDRAM
Video Card:ASUS GeForce 7600GS (AGP 4x)
Sound Card:On Board sound
HD: WD1600AAJB
Remote: None (yet)
Tuners:HDHomeRun

Performance
Combined FE/BE.  Within the MythTV interface, playing SD recordings, I'm in good shape.  If I try to watch something from an HD channel, video is choppy and the sound is like... well when you pretend to be underwater and you move your finger between you lips.  It's like that :).

If I open VLC and play the same recording with MythTV closed, it is smooth (except for a hiccup every 20 s or so...).  I've played a bit with the settings in Myth but I can't seem to find the proper sweet spot for my system.  Do you think the processor is just too slow?  Where should I start to find out where the bottleneck is?  I just bought the video card, HD, and the HDHomeRun and now I'm wondering if I should have skipped the video card and HD and just bought a new, cheap system from Dell or something.  I'd like to get this working so this box can retire as a PVR.  Am I asking too much of the old man?

For what it's worth, I have been able to watch *live* HD from my Macbook FE over my wireless network flawlessley, but that was before I did this fresh install of 7.10 on my new HD.  Now, it looks like the BE/FE databases don't match up, so I need a new MythFrontEnd for my Mac.

Thanks all!

---

### Post by Trollslayer on 2008-04-13
A P4 1.3GHz is going to suffer when you try HD, I'd reccommend a 2.8GHz P4 minimum and VLC.
With a Core Duo E6420 (dual core 2.33GHz) and ATI x1250 the internal play is a bit jerky at 720p, VLC is smooth at any resolution.

---

### Post by jweida on 2008-04-14
Thanks a lot for your response.  Looks like it's time to spec a new machine.

---

### Post by temujin77 on 2008-04-14
If you are suspecting hardware inadequacies, perhaps you can try to play something smaller/lower quality/older, if possible.  See if that runs smoothly.  If so, then it might be another sign that the CPU you're using isn't powerful enough to decode higher quality stuff we tend to use today.

---

### Post by Caps18 on 2008-04-15
Have you tried changing the default player from mplayer to VLC or Xine in MythTV?  I can look up the command line I use tonight if you like, or you can search the forums here for it.  I got it here from someone else.

I have a few problems playing mkv files inside MythTV using Xine, but if I watch them outside of MythTV it works ok.  I have no problems with my 1.6Ghz machine watching 1080i recorded TV though.

---

### Post by balserodeluxe on 2008-07-15
Guys, I have the very same problem and I would be a happy "Mythbunter" with VLC if I could get it to be the default player. I followed the instructions on [http://mythtvbox.blogspot.com/2006/10/switching-from-mplayer-to-vlc.html](http://mythtvbox.blogspot.com/2006/10/switching-from-mplayer-to-vlc.html) but it does not seem to work. The command here is stated to be:


vlc file://%s vlc:quit

But it does not change anything for me, even after a reboot.

---

### Post by newlinux on 2008-07-15
> **balserodeluxe said:**
> Guys, I have the very same problem and I would be a happy "Mythbunter" with VLC if I could get it to be the default player. I followed the instructions on [http://mythtvbox.blogspot.com/2006/10/switching-from-mplayer-to-vlc.html](http://mythtvbox.blogspot.com/2006/10/switching-from-mplayer-to-vlc.html) but it does not seem to work. The command here is stated to be:


vlc file://%s vlc:quit

But it does not change anything for me, even after a reboot.

Unless something has changed in .21 (I use .20.2 still) changing your default video player only affects mythvideo, not your myth recordings. You recordings have to use the "internal" player (which is neither VLC nor mplayer).

---

### Post by balserodeluxe on 2008-07-17
Thanks newlinux,

it is not a fix but kinda clarifies things.

---

### Post by 7.11brown on 2008-10-24
I have a similar problem, EVERYTHING is choppy.  the news is like this:  To..nigh..t.. at..six..a 1 second pause every 2-3 seconds.  EVERYTHING is choppy in the way of programs through myth.  If i open the file through any program without myth open, all is good, but not when playing through myth.  

my specs
2.8 ghz Celeron D 64 bit
512 mb ram
500 & 80 gb hdd

SDTV is fine, but once i go to HD, all is chopped, and i can't play the music channels that my other hdtvs can get (free unencrypted).  Myth found them, but this is beside the point.

---

### Post by anonymousdog on 2008-10-24
Is that frontend only?...frontend/backend?  Video card/chipset?

Experiment with different playback profiles (and XvMC if you have a supported nVidia video chipset/card) and, if that doesn't get it, double your memory or post back frontend log snippets along with resource utilization summaries from choppy playback attempts.  That machine may be a bit short on memory to playback HD smoothly; MythTV uses more resources than I've seen in a Linux environment for any software this side of big enterprise database apps...even our heavily loaded anti-spam gateways don't stress the hardware like a simple MythTV box does.

---

