---
title: "Turn Off Pulse Audio"
date: 2009-04-24
forum: Multimedia Software
---

### Post by Frihet on 2009-04-24
I am presently installing 9.04 NBR on a Sylvania G Meso.

Is there a way to turn Pulse Audio off. I want to do some recording, and my experience is that Pulse Audio really messes things up (snap, crackle, pop, buzz).

Thanks!!!

***

OK, I found it. Just set all options to ALSA. I'll see how that works. Perhaps that is enough to disable Pulse Audio and the packages will not have to be uninstalled. I've heard that may break things.

---

### Post by psyke83 on 2009-04-24
> **Frihet said:**
> I am presently installing 9.04 NBR on a Sylvania G Meso.

Is there a way to turn Pulse Audio off. I want to do some recording, and my experience is that Pulse Audio really messes things up (snap, crackle, pop, buzz).

Thanks!!!

***

OK, I found it. Just set all options to ALSA. I'll see how that works. Perhaps that is enough to disable Pulse Audio and the packages will not have to be uninstalled. I've heard that may break things.

Setting the options to ALSA in System/Preferences/Sound does not do what you think.

First of all, that application only controls GStreamer applications (Totem, Rhythmbox, etc.). Other applications will not be affected.

Secondly, even if you change to ALSA output for that limited set of applications, they will continue using PulseAudio, as it has been configured to "intercept" ALSA output.

My advice is to give PulseAudio a chance in this new release, as many improvements have been made.

---

### Post by JC Cheloven on 2009-04-27
> **psyke83 said:**
> 
My advice is to give PulseAudio a chance in this new release, as many improvements have been made.

Nope. Still you can't record your voice with "sound recorder" from your built-in microphone (for example). 

Gnu-Linux will not be a feasible option for digital audio workstations until the the very basics of sound are clarified. PA was supposed to come in for this, but things have become even worse.

---

### Post by Arup on 2009-04-27
Skype works fine here, I have done countless recordings of sound with Audacity and that too works out quite well.

---

### Post by markbuntu on 2009-04-27
Do this

[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

---

### Post by dugh on 2009-08-30
How do we turn it off then.

I get crackling after a while in Audacious and then the system freezes sometimes.

---

### Post by DouglasAWh on 2009-10-15
> **dugh said:**
> How do we turn it off then.

I get crackling after a while in Audacious and then the system freezes sometimes.

I'd also like to know how to do this...except in Karmic...and I know the sound preferences have changed there.

---

### Post by andied on 2009-10-15
I removed pulseaudio in karmic and had no sound - about to go back to jaunty...or XP - I am tired of fighting with it.

---

### Post by DouglasAWh on 2009-10-15
> **andied said:**
> I removed pulseaudio in karmic and had no sound - about to go back to jaunty...or XP - I am tired of fighting with it.

Well, I'm sure you're aware, but Karmic isn't finished yet.  Unless you're interested in developing or QAing, I'd definitely not suggest working with the alphas/betas.  Seems as though this dev cycle has been worse for breakage than Jaunty, but maybe that's just my personal experience.

---

### Post by DouglasAWh on 2009-10-15
> **andied said:**
> I removed pulseaudio in karmic and had no sound - about to go back to jaunty...or XP - I am tired of fighting with it.

oh, also, just to clarify, you uninstalled it right, didn't just turn it off?

---

### Post by andied on 2009-10-15
I followed advice I found: "sudo apt-get purge pulseaudio" , if that is the way to do it.

I understand karmic is still beta, but I tried it because I found jaunty used relative high system resources to play audio and karmic is considerably lighter on resource usage, but perhaps that is a result of pulseaudio in karmic, but I removed it in jaunty. I have an intel hda and have never been able to get the digital mic to work with pulseaudio - I know I am not alone.

---

