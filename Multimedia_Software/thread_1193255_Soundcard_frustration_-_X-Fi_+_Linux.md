---
title: "Soundcard frustration - X-Fi + Linux"
date: 2009-06-21
forum: Multimedia Software
---

### Post by Silent Warrior on 2009-06-21
Ok, it's that time again - mentioning the X-Fi and Linux in the same sentence tends to lead to a cataclysmic explosion. Though my... frustration is... great, I'll try to rein myself in.

The catch, as such, is that with the recent kernel-update (.12 to .13) my sound went away - I know, I know: more fool me for updating and I should bloody well roll back - and wouldn't come back because Creative's driver-like release only compiled into something that gives me the mother of all noises coming out of my speakers. (And now that I've changed speaker-configuration, the noise was... massive. Proper amplifier + four fair-sized speakers all within two yards of me.)
After poking around Creative's forum, I found a reference to a kind of breakthrough with X-Fi-support and Linux, though - apparently someone got in touch with Creative, who may have acknowledged defeat, and was given a number of things that enabled him to make a proper driver. I'm not sure what version of ALSA would include this (1.0.20 or 22 was mentioned), but I suppose it's only a matter of time.

But, I'm MAD! :evil: So, I've semi-decided to 'do the right thing' and replace my current soundcard (X-Fi Extreme Music) with one of ASUS' Xonar D1 (not D2 - frightfully expensive, though no doubt worth most of the pennies).
So... is this a wise thing to do? Apparently, the Xonar might only(?) support up to EAX 2, while the X-Fi goes up to EAX 5. I don't believe this matters a whole lot to me (I think the only game I play that actually claims to use EAX 5 is NWN2) - I'm more concerned with whether it works or not, and by looking at ALSA's compatibility-list, the Xonar D1 whips major X-Fi hide in this respect. Like I hinted at, my current speaker-configuration is with a conventional stereo-amplifier, effectively a four-point stereo improvisation (heh, you should really see this, there's no sense in it of any persuasion), so 5.1 or 7.1 support won't matter for the time being.
I've also looked at some other soundcards (M-Audio Revolution 5.1/7.1, Club3D Theatron and Xonar D2 - these are the only four non-Creatives I can find in a physical hardware-store near me) and thought ASUS' bid suited me better. I have plans to attach a home-cinema rig to it at some point, and the option to have optical... well, at least OUTput has a certain appeal. (Not that I have anything against S/PDIF or co-ax, or would be able to hear any difference...)
(I only use optical in randomly while playing PS2, so it's not a big deal to lose that option.)

Let the masses have their say while I roll back my kernel...

By the way, I have business to the store that offers the Xonars next week - my parents want some new RAM for their old bugger. PC2100, 1 Gb in total (and only two slots available!), and a USB2-controller card. :) Thought I'd take care of all of it in one go.

---

### Post by ssam on 2009-06-21
support seems to have just entered the mainline kernel. so when kernel 2.6.31 is released your card may just work.

> Sound: Wolfson Micro WM8988, WM8940, WM9081, and WM8960 codecs, Digigram LX6464ES boards, ESI Maya44 boards, several Creative Sound Blaster X-FI devices based on the 20K1 and 20K2 chipsets, a USB Audio gadget driver. 
[http://lwn.net/Articles/336953/](http://lwn.net/Articles/336953/)
(LWN is subscriber only for the latest articles, so you will either have to wait until next thursday to read, or check you private messages).

i recommend you wait a couple of weeks until the kernel development settles back down a bit and then try a mainline kernel [https://wiki.ubuntu.com/KernelMainlineBuilds](https://wiki.ubuntu.com/KernelMainlineBuilds)

---

### Post by Silent Warrior on 2009-06-21
Right, PM received and read. And I'll confess a slight excitement about this new kernel. The soundcard will wait.

[Edit] And after compiling against the earlier kernel, all is well again, and I won't need a new soundcard. I got myself a CPU-fan instead. :)

---

