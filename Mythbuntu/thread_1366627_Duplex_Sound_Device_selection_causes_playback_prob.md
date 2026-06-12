---
title: "Duplex Sound Device selection causes playback problems"
date: 2009-12-28
forum: Mythbuntu
---

### Post by Zeedok on 2009-12-28
I updated from Mythbuntu 9.04 to 9.10 on my HTPC.  Here are my hardware specs:

Antec Micro Fusion 350 HTPC Case
Intel Core 2 Duo E8400 CPU 3.0 GHz
Gigabyte GA-EG41M-S2H Mainboard
4GB DDR2 PC6400 (2x2GB) Dual Channel RAM
8X Dual Layer DVD+RW + 20X DVD+-RW + CD-RW Combo Drive
1TB 7200RPM SATA HDD
512MB NVIDIA Geforce 8400GS
Gigabit Ethernet
Hauppauge Nova-T-500 MCE Dual DVBT SD/HD tuner

As far as I know, I am running with the onboard (HDA Intel) soundcard and I have ALSA 1.0.20 installed.

I have been having a couple of issues with video and flash video playback (see [here]("http://ubuntuforums.org/showthread.php?p=8572552#post8572552") and [here]("http://ubuntuforums.org/showthread.php?t=1360390") for my other threads) and I have narrowed my problem down to my choice of sound device profile.

Essentially, in order to get sound output (connected to my home av receiver via an optical output) I have to choose "Digital Stereo Duplex (IEC958 )".  This gives me sound output from Mythtv frontend, but with myth running, video playback in movie player (aka totem) on ubuntu desktop does not work (it gets stuck on the first frame) and flash video is unstable (some video sites do not load properly, youtube often causes firefox to hang).  If I close mythfrontend, or select another sound profile (which means I lose sound of course), both of these issues diappear.

Originally, I thought these were seperate issues.

What I need to know is:

1.  Which sound profile should I be using to get sound (digital 5.1 when appropriate) and to allow other programs to access the sound card while myth is running.
2.  Should I change a preference within the myth setup itself to correct this issue
3.  Is there another work around?

Thanks for any help.

---

### Post by Zeedok on 2010-01-01
OK - so in attempting to update ALSA I seemed to have caused a few "kernel panics" so I did a clean reinstall (now Ubuntu 9.10 with Myth added after).  My sound issues persist.

In short:

By selecting "Digital Stereo Duplex ( IEC958 )" as my hardware device I can get sound for myth and the rest of my system, but if mythtv frontend is running, flash stutters and causes firefox to hang.  This is resolved when I close myth frontend.

Also, I have a Windows MCE remote for the myth system, but changing the volume within myth no longer works.  In fact, I can't find a volume control slider that changes the volume (either with the defult sound config tool or with gnome-ALSA mixer).

Any suggestions?

---

### Post by Zeedok on 2010-01-04
Bump

---

