---
title: "How do I enable direct rendering?"
date: 2009-03-06
forum: Multimedia Software
---

### Post by NoranaC on 2009-03-06
I'm trying to figure out how to enable direct rendering.  My graphics card is VGA Jaton nVidia Geforce 7600 256MB.  I am using nVidia driver version 177.82 but I have also tried v. 173 and 96 and I am on Intrepid.

I've been all over the forums and tried about a dozen different things to get it DRI-enabled but they don't seem to work.  Either I just get some Fail error or my monitor goes into low graphics mode and lays down on the floor twitching with its legs in the air.

I was on Hardy until last week and my video card was DRI-enabled but when I upgraded, no more.

Any and all assistance is greatly appreciated!
Thank you
-Norana

---

### Post by NoranaC on 2009-03-07
Ok, so when I try "glxinfo | grep rendering" I get the following:
"NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).
direct rendering: No"
So I tried "sudo glxinfo | grep rendering" and I get "direct rendering: Yes"

Does this mean that I have direct rendering enabled, or that it is on enabled when I have root access, or what?  The nVidia X Server settings also say "Driect Rendering:  No" so I am inclined to believe that I do not have it enabled but that this is the reason why everything that I try to enable doesn't work properly.  But I don't really know...

Thank you.

---

### Post by dcstar on 2009-05-01
> **NoranaC said:**
> Ok, so when I try "glxinfo | grep rendering" I get the following:
"NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).
direct rendering: No"
So I tried "sudo glxinfo | grep rendering" and I get "direct rendering: Yes"

Does this mean that I have direct rendering enabled, or that it is on enabled when I have root access, or what?  The nVidia X Server settings also say "Driect Rendering:  No" so I am inclined to believe that I do not have it enabled but that this is the reason why everything that I try to enable doesn't work properly.  But I don't really know...

Thank you.

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/370249](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/370249)

---

