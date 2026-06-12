---
title: "Sound Output internal or external speakers or headphones"
date: 2010-07-18
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by thonuz on 2010-07-18
Hello,

I have a sound problem. I am pretty sure it is related to hardware and was curious if anyone had a similar problem. 
On laptop with Intel (older Sony Vaio duo core) I get no sound with speakers when plugging them into headphone jack but laptop's internal speakers work.
On an i5 notebook with Nvidia graphics (not sure about the card off hand) I get the opposite: only external speakers or headphones give me output. 
None of the sound preferences change anything.
Bug in each one or wait it out?
:popcorn:

---

### Post by dmiracle74 on 2010-07-19
> **thonuz said:**
> Hello,

I have a sound problem. I am pretty sure it is related to hardware and was curious if anyone had a similar problem. 
On laptop with Intel (older Sony Vaio duo core) I get no sound with speakers when plugging them into headphone jack but laptop's internal speakers work.
On an i5 notebook with Nvidia graphics (not sure about the card off hand) I get the opposite: only external speakers or headphones give me output. 
None of the sound preferences change anything.
Bug in each one or wait it out?
:popcorn:

It could be a driver issue.  Do you have windows on these laptops?  If you do does the problem happen in wndows?

I know on my HP desktop (came with Vista) if I plug in ear buds to the front jack it disables to rear jacks that are connected for my desktop speakers.  My front jack stopped working a couple months ago.  I found out via HP tech support that there is a setting in driver/software to detect when something is plugged in.

I would test this in my ubuntu but I never got the front jack working because my computer is out of warranty.

Dale

---

### Post by jfernyhough on 2010-07-19
Sounds like a hardware driver quirk is needed. My Dell 1749 needs an option in /etc/modprobe.d/modules.conf :

option snd-hda-intel device=dell-m6-dmic

Without this the internal speakers work but plugging in headphones mutes both internal speakers and headphone jacks. With this behaviour is as expected.

---

### Post by thonuz on 2010-07-19
I just installed Kubuntu-desktop and my laptop speakers and external/headphone now work.
This could be because I got something else in the update. VLC, Totem and Kaffeine all now work and my GUI sound settings are the same. Oddly I have this problem with 10.4 and I never got round to fixing it and just plugged in speakers instead. 
I hope this don't break in future update: this is on an Intel 5 series with nvidia geforce 310 and 02:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1) -- Just checking sound preferences: set to internal audio analog stereo. HDMI don't work -- too early to tell on all this.

---

