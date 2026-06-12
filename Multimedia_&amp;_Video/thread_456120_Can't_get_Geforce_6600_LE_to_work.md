---
title: "Can't get Geforce 6600 LE to work"
date: 2007-05-27
forum: Multimedia &amp; Video
---

### Post by Poman on 2007-05-27
My card (AGP) even in Windows XP seems to work only with the drivers it came with on CD. After trying a lot of things, I finally got it to work in Ubuntu 6.10 AMD 64 only with Envy. I tried upgrading to Ubuntu 7.04, and that halted, then tried reinstalling three times after trying all various drivers in synaptic and nothing works, not even Envy manually. Envy doesn't work for me anymore.

Could it be a problem with my motherboard bios settings? AGP vs. PCI, anything else? I've got a GA-K8NSC-939 motherboard with nForce3 250Gb chipset, and the Athlon 64 3200 processor.

I'm wondering if I can flash my video card bios up to something kind of generic. Right now I can only get it going in VESA mode... it'd driving me nuts, and the guy who sold me the video card said it's the most compatible card ever. I guess I was fooled.

The manufacturer of the card is Arcade FX. It seems Ubuntu doesn't recognize my SyncMaster 970p monitor as well, could this cause a conflict?

Many thanks in advance! I've had a taste of Ubuntu and Beryl, and I want more...

---

### Post by darrglud1 on 2007-05-27
You could try to download compatible drivers from nVidias website, because that should fix your problem. Otherwise, you could code your own driver (actually you would benefit from it, and so wouldn't the community).

---

### Post by Poman on 2007-05-27
I might consider that actually... My video card's manufacturer has a specific driver linked to one of the versions on the nvidia site, but I still don't know how to install those manually.

---

### Post by tseliot on 2007-05-27
Make sure you use Envy's latest release (0.9.3-0ubuntu6)
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by Poman on 2007-05-27
Thank you!

I'm thinking of installing Ubuntu 6.06. The first one I tried was 6.10, and Envy worked fine there, though it was the ONLY thing that worked. Then it got worse with 7.04. I'm still in vesa. I tried the stable Envy too, but to no avail. I've even tried flashing my motherboard to an earlier bios version...

---

### Post by Poman on 2007-05-27
I'm running 6.06 now, and I have full 3D accelleration with the nvidia-glx driver in synaptic... sadly Beryl is not compatible with this older version. :(

---

### Post by Poman on 2007-05-30
I'm still trying everything, but this time I'm not giving up on Feisty Fawn. I'm using the nv driver now. It seems that any of the nvidia drivers I install recognize my card, but gdm won't start because the drivers don't "trust" my SyncMaster 970p LCD monitor. I've tried entering the frequency specifications in the xorg.conf, but that doesn't help. With older drivers such as nvidia-glx, I get a message that the card found the monitor but can't work out a configuration for it. With all newer drivers, including whatever I try from Envy or Automatix, I just get a black screen right after the initial Ubuntu screen and it appears to be frozen... not respond to keys.

---

### Post by ihc100 on 2007-07-30
Has been a while but anyway.
Did you achieve something?
I'am having the same problem here, spend three days to figure it out, still it works only with the "nv" driver, without GLX.
I only know its the motherboard because i have tried several graphic cards, must use a feisty driver because the system must stable.
If I find something i will post it here.
w.k.r.

---

### Post by domnin on 2007-10-28
Same problem here. Geforce FX 5700 ultra. My guess is that it's the motherboard that is 
to blame.

Have you come to any resolution?

---

