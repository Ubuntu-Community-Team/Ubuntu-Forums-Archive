---
title: "Display on TV (second video output not correct)"
date: 2009-04-13
forum: Multimedia Software
---

### Post by GammaPoint on 2009-04-13
Hi, I think this is something that became a problem when I upgraded from 8.04 to 8.10 and 9.04 (the latter two upgrades happened on the same day so I'm not sure which one originally caused it) but the tv that my computer outputs to as a second display doesn't fill the entire TV screen anymore. Instead there is probably a 1-2 inch wide vertical black section on the right side of the screen. I imagine it's some simple display configuration that I need to change but I'm not sure because with 8.04 it 'just worked' and I never had to think about it. Anyway, what should I do to fix this?

Thanks for your help!

---

### Post by Kareeser on 2009-04-13
Please do a test for me.

Open up a terminal window and drag it up and down, to the left and right. Do you see artifacting? My guess is you do.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/355761](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/355761)

That bug should be what you're experiencing. Your feedback would be appreciated :)

I personally believe it is a compiz regression... but it could be anything. Unfortunately, Jaunty's in a freeze right now in prep for the RC, but if we can convince the devs that this is a serious problem, they'll work on it.

Also, paste the output of this command for me:
```
lshw -C video
```

---

### Post by GammaPoint on 2009-04-13
Thanks for the quick response Kareeser. I've done the two tests that you asked.

First I'm not sure about what 'artifacing' is exactly, but when I move my windows up and down nothing looks out of the ordinary. I have 'wobbly windows' on and everything looks as smooth as normal.

Here is the output of the lshw command:

```

  *-display               
       description: VGA compatible controller
       product: GeForce 8600 GT
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia


```

Thanks again for any help you can give me :)

Edit: I just looked at the screenshot of 'artifacing' in the launchpad link you gave. I definitely don't see that.

---

### Post by Kareeser on 2009-04-16
Hm. That may or may not be because you're using a decent video card. I'm experiencing the same problem, except I have an onboard intel video card.

Does nvidia-settings report as outputting the proper resolution? Or is it defaulting to a different one for one reason or another?

With me, while xrandr reports it as outputting the correct resolution, I don't see that happenning on the TV...

---

### Post by sharon.gmc on 2009-04-17
I am also experiencing the same problem. Please help me.:(

---

### Post by GammaPoint on 2009-04-17
> **Kareeser said:**
> 
Does nvidia-settings report as outputting the proper resolution? Or is it defaulting to a different one for one reason or another?
.

Well I've got an 37LG30 and the resolution is 1366 x 768 on that say the specs online and when I check out nvidia-settings the resolution is set on 1360 x 768 so I guess that's right?

I think this problem may have started happening when I upgraded from 8.04 to 8.10 and updated the nvidia driver, but I'm not sure. This is just a guess.

---

### Post by GammaPoint on 2009-04-25
Any other ideas? :(

---

### Post by wolfen69 on 2009-04-25
something probably got borked during the 2 upgrades. a clean reinstall will probably help.

---

### Post by GammaPoint on 2009-05-16
Does anyone have any other ideas? Think it could be the nvidia driver?

---

