---
title: "Soundcard works in 11.04 but not 11.10 (I would really like it to work)"
date: 2012-01-18
forum: Multimedia Software
---

### Post by larrypg on 2012-01-18
Hello all,

I have a Creative SB X-fi Xtreme PCIE sound card.  I have very very,very,very, choppy sound with any version of 11.10. I would like to at least try (with sound) 11.10 or 12.04 but have to keep going back to 11.04. I have installed K,U,X, buntu and none work in 11.10.    

I have not only disabled sound from my cpu but I do not have any way of inserting plugs into anything (other than hdmi) except my soundcard.  

Alsa says that it is (and won't be) supported) because of pcie.

Sound works fine in a Virtualbox install of 11.10 but it does not show the Creative card. It is showing it is working off the pcu which although it is diabled in the bios is probably another question. 

Since I know that sound works fine in a Virtualbox install but does not in a real install it makes it a bit difficult to try and figure out what the differences are between 11.04 and 11.10 (or maybe 12.04).  I have to install 11.10 then install 11.04 again  and then try and figure out what the difference is. 

Just to sum things up:
Sound works fine in 11.04 and detects and installs drivers for my Creative SB X-fi Xtreme Pcie.

Virtualbox install of 11.10 works fine but does not show my real soundcard.

Any install of 11.10 (except Virtualbox)  does not give me anything but very choppy sound. 

I have been trying to work on this since October and have had no luck so far (after countless installs).  

Any help would be appreciated.

---

### Post by larrypg on 2012-01-18
Sorry for the double post

---

### Post by wolfen69 on 2012-01-18
> **larrypg said:**
> 
Sound works fine in 11.04 and detects and installs drivers for my Creative SB X-fi Xtreme Pcie.
Why not stay with it? There's not much difference between 11.04 and 11.10 Then try 12.04 when it is released.

> Virtualbox install of 11.10 works fine but does not show my real soundcard.
That's because vbox uses it's own sound card, in a sense. It does not use your hardware per se, but emulates generic hardware devices. That way, vbox does not have to account for 1000's of different hardware devices, but can supply drivers for a couple different sound devices that are emulated.

In other words, you never have to worry about getting driver support.

---

### Post by larrypg on 2012-01-26
Hello,

As I must be a glutton for punishment I decided to try another install of 11.10 and spent the last day searching and trying different things but no luck.  

Just as an aside...Youtube will not work because of the soundcard.  Both sound and the video stutters badly but if I disable the soundcard the video works fine (but of course no sound).  

Wish I could figure out (or someone let me know) what has changed between 11.04 and 11.10. 

Well I guess I will try for another day or so and then back to 11.04.

---

### Post by znajem on 2012-04-27
I installed 11.10 on a similar machine as the one indicated here and had a similar problem with the sound-card. The problem was solved after consulting [https://wiki.ubuntu.com/Audio/PositionReporting](https://wiki.ubuntu.com/Audio/PositionReporting), section (Turning off PulseAudio timer scheduling).

In specific, I did the following
> 
If your problem is specific to [PulseAudio]("https://wiki.ubuntu.com/PulseAudio"), you could as a last resort, try to turn off PulseAudio's timer scheduling. Note that this might consume slightly more power. 

To change this, edit the file /etc/pulse/default.pa and change the line that says: 

load-module module-udev-detect

to 
load-module module-udev-detect tsched=0

After editing the file, reboot your computer for changes to take effect.  

---

