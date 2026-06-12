---
title: "Just Purchased Nvidia 7100GS PCIe Card, Need Assistance"
date: 2007-01-16
forum: Multimedia &amp; Video
---

### Post by jlacroix on 2007-01-16
Hello everyone! My explanation may be kinda long so please bare with me. :)

I used to have a BFG  NVidia Geforce FX AGP video card with 256MB of VRam. From glxgears, it gave me a framerate averaging 2800fps.

I purchased a new motherboard, MSI K9VGM-V. Unfortunately it does not have an AGP port, so I could no longer use my BFG Geforce FX card. In the meantime I decided to temporarily use my PCI Geforce 2 card that gave me a measilly 800 (and below) fps in glxgears.

Today I finally purchased a PCI Express (PCIe16) card, an MSI NVidia 7100GS card which is also 256MB of VRam like the BFG NVidia card I used to have. It has something called "Turbo Cache". (I'm not sure what that is).

I didn't change anything in my xorg,  (when I get home I can post my xorg conf if required) I just plugged in the card and booted up. It seemed to go fine. Now my fps in glxgears is up to 1400fps, good, but not like the 2800+ fps I used to get with the AGP card I used to use that was also 256MB.

This is the very first time I ever used a PCIe video card, so I am a newbie. I'm a pro at setting up the bios settings for AGP but know nothing of the bios settings for PCIe. I also know nothing about what I should have in my xorg conf file for PCIe.

So in summary here are my questions:

1.) Should I have reinstalled the nvidia-glx driver since I have a new Nvidia card now, or does the NVidia kernel module automagically update itself?

2.) What should I do in my BIOS to make it work as best as it (stabilly) can? Since I am now using PCIe I am not sure if this is all the same as AGP, I didn't get a chance to check anything before I was due at work.

3.) What is turbo cache, and does Ubuntu make any use of it?

4.) Since I am PCIe now, is there anything special that I should put in xorg to increase performance or is it exactly the same as before?

5.) I didn't remove my previous Geforce 2 PCI card. Does that absorb any resources?

Thanks everyone! I really appreciate any help I can get with this.

---

### Post by tseliot on 2007-01-17
I have moved the thread to a more appropriate place.

---

### Post by tseliot on 2007-01-17
> **jlacroix said:**
> 1.) Should I have reinstalled the nvidia-glx driver...?.
No

> **jlacroix said:**
> 2.) What should I do in my BIOS to make it work as best as it (stabilly) can? Since I am now using PCIe I am not sure if this is all the same as AGP, I didn't get a chance to check anything before I was due at work.
just make sure that PCI-E is selected instead of PCI

> **jlacroix said:**
> 3.) What is turbo cache, and does Ubuntu make any use of it?
have a look at this:
[http://en.wikipedia.org/wiki/Turbo_Cache](http://en.wikipedia.org/wiki/Turbo_Cache)

> **jlacroix said:**
> 4.) Since I am PCIe now, is there anything special that I should put in xorg to increase performance or is it exactly the same as before?
Make sure you have the latest release of the Nvdia driver and type:
```
sudo nvidia-settings
```

then set things such as antialiasing and antisotropic filtering to your liking


> **jlacroix said:**
> 5.) I didn't remove my previous Geforce 2 PCI card. Does that absorb any resources?
I guess not

---

### Post by jlacroix on 2007-01-17
Thanks!

I'm getting horrible framerates though, does anyone else have a 7100GS and can tell me what framerates they get?

---

