---
title: "The minute I uninstalled Pulseaudio, crashes stopped. Why do we use it?"
date: 2012-02-23
forum: Multimedia Software
---

### Post by videodrome on 2012-02-23
My fresh Xubuntu 64 install lately was just randomly dumping me out to a unusable shell or error text screen, and giving me that "pulse audio single user session error."

I was also having Flash issues where a person's lips weren't synced with the audio, as well as quiet sound and random lockups.

Last night I uninstalled Pulseaudio. The minute did so, and simply defaulted back to the ALSA that was already installed, everything now seems to be running great and seemingly faster.

And no audio errors in any apps at all. Flash works in Firefox, VLC works, etc.

So why do we use Pulseaudio? As far as I can tell, there are a ton of people on the Web who hate it and and aren't a fan of the developers, *and* it's really buggy.

Thanks

---

### Post by jocko on 2012-02-23
> **videodrome said:**
> So why do we use Pulseaudio?
Because it's the only reliable (well, for most people at least) way of getting decent quality sound from more than one application at the time?

Unless you are lucky enough to have one of the extremely rare sound cards with working hardware mixing (must be both present in hardware and supported by alsa), you need some software mixer.

Alsa does have a software mixer (dmix), but it's a hassle to set up and lags and degrades the sound quality noticeably.
Pulseaudio just works (for most people), and its quality is better than dmix. That's why we use it.
But no solution is perfect. Some people are having trouble with it. 
I'm sure the amount of people that have no trouble at all with pulseaudio, but would have trouble without it is larger.
So ditch pulseaudio to help a few unfortunate ones, at the same time messing things up for more people? I think you can guess what the answer is.

---

### Post by ajgreeny on 2012-02-23
> **jocko said:**
> Because it's the only reliable (well, for most people at least) way of getting decent quality sound from more than one application at the time?

Unless you are lucky enough to have one of the extremely rare sound cards with working hardware mixing (must be both present in hardware and supported by alsa), you need some software mixer.

Alsa does have a software mixer (vmix), but it's a hassle to set up and lags and degrades the sound quality noticeably.
Pulseaudio just works (for most people), and its quality is better than vmix. That's why we use it.
But no solution is perfect. Some people are having trouble with it. 
I'm sure the amount of people that have no trouble at all with pulseaudio, but would have trouble without it is larger.
So ditch pulseaudio to help a few unfortunate ones, at the same time messing things up for more people? I think you can guess what the answer is.
+1

I have not had any problems with pa once I realised that there are a few pa packages that for some reason are not installed by default in Lucid 10.04, and it has certainly never crashed my system.  I had to install **pavucontrol** and **padevchooser** in order to get the configuration options that I needed for pa to work properly, and I still need to have alsamixer available to ensure that sound levels and volumes are correct.

Look to see if those packages are available to you, though I think padevchooser is no longer a separate package for 11.10, so it may already be in the system under another name.

---

### Post by Yellow Pasque on 2012-02-23
If you don't like it, don't use it. At least you have xfce/xubuntu where it isn't coupled so tightly with the desktop environment.

> Alsa does have a software mixer (vmix)
Actually, it's known as dmix.

> it's a hassle to set up and lags and degrades the sound quality noticeably.
Distros often set up dmix automatically with config files and I've seen ALSA devs claim a lot of the issues with it have been fixed. No personal experience with it though..

In case you're wondering, I use pure ALSA on my main OS (Debian). I ran pulse for a while, but it had little value to me since I have a card with hardware mixing.

---

### Post by Rallye on 2012-02-23
PulseAudio solved every "out of the box" issue I had. Using the GUI just a few minutes ago resolved a through browser audio issue I had with my headset.

---

### Post by videodrome on 2012-02-23
Thanks for the feedback guys, I do appreciate it. 

I guess I never realized why Pulseaudio was needed since I can, with just ALSA on a fresh Xubuntu installation, play a flash file or youtube video in Firefox and then play an mp3 in VLC and have them both work simultaneously.

I did not realize that other people cannot do this, or that doing so doesn't just usually work right out of the box.

---

