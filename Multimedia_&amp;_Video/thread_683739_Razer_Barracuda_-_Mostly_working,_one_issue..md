---
title: "Razer Barracuda - Mostly working, one issue."
date: 2008-01-31
forum: Multimedia &amp; Video
---

### Post by Symmetriad on 2008-01-31
Hey everyone - first post in Ubuntuforums here. :)

I recently got a Razer Barracuda sound card (thanks to a rather cheap woot.com deal), which is based on the C-Media CMI8788 chip. This is now supported in beta RC ALSA drivers, so I figured I'd give it a go in my Ubuntu system.

The good news is, everything seems to be working, including SPDIF optical out. The bad news is, every time a new sound thread is started - e.g. a game, an Amarok playlist, etc. - the first quarter second gets cut off, after which everything is fine. Also, SPDIF out seems to uncheck itself in the mixer every time I reboot.

Any advice on how to resolve these issues? I'm willing to live with this relatively minor bug, but if there's a way to resolve it I'm more than willing to give it a shot. :)

---

### Post by proteo on 2008-01-31
have you tried the newest driver? [http://www.alsa-project.org/main/index.php/User:ClemensLadisch]("http://www.alsa-project.org/main/index.php/User:ClemensLadisch")
This driver it's improving very fast, I think it could be totally finished by the final release of the 1.0.16 drivers.

---

### Post by Symmetriad on 2008-01-31
> **proteo said:**
> have you tried the newest driver? [http://www.alsa-project.org/main/index.php/User:ClemensLadisch]("http://www.alsa-project.org/main/index.php/User:ClemensLadisch")
This driver it's improving very fast, I think it could be totally finished by the final release of the 1.0.16 drivers.

I didn't know one just came out yesterday, but I did use the latest beta/RC driver previous to that - alsa-driver, alsa-lib and alsa-utils. However, I'm new to compiling from source, and I don't believe I used any switches when doing ./configure for alsa-driver, nor did I use the modprobe command at all (I read up more on the sound driver install process after the fact)... so I may have made a mistake there.

---

### Post by proteo on 2008-01-31
I just compiled that last version, without any switches, just ./configre, make, sudo make install, and  restarted, it's working fine with my sound card.

---

### Post by Symmetriad on 2008-01-31
> **proteo said:**
> I just compiled that last version, without any switches, just ./configre, make, sudo make install, and  restarted, it's working fine with my sound card.

That's the same process I went through to install them as well. Maybe I'll give the new drivers a shot once I get home, then. Would I need to do anything to uninstall the old versions?

---

### Post by proteo on 2008-01-31
Personally, I haven't uninstalled older versions, just installing new ones; but I have been dragging this problem since I got the sound card (before there was a proper alsa driver and since the oss beta driver), I only have some programs and sounds working on my system, maybe because I have been tinkering with sound since last 2 releases of Ubuntu, just upgrading between releases and not doing a clean install. I'm going to reinstall for the next release, and I hope that will fix my sound problems under Linux. :lolflag: 
I guess OSS and ALSA don't mix very well :)

---

### Post by krylon on 2008-02-09
Have you two gotten your Mic to record in Ubuntu? I am running Alsa 1.0.16 and everything works except the Mic when I test it using Sound Recorder.

---

### Post by GG_HTPC on 2008-04-04
I have been trying to get my Azuntech Meridian to speakup anything in any application using the SPDIF out - no luck so far.

I have tried detailed sticky by Lord Radien and the Oxygen post on ALSA (I get permission denied errors in .configure step). I have even tried to install OSS from 4front. Unfortunately, no luck. Maybe I am missing something.

Can you please post the steps you took to install and configure the CMI8788 based card. 

Thank you in advance.
:confused:

---

