---
title: "How to configure 3 monitors"
date: 2011-08-23
forum: Multimedia Software
---

### Post by Scottty on 2011-08-23
Hello

I have set up 3 monitors with Ubuntu. Something I could not do with Windows XP or Windows 7. I was very impressed.

The only thing I would like to change is the Menu Bar that runs down the left side of the middle screen, (monitor number 2). 

I would like it to be on the very left side of the 1st monitor (monitor number 1).

Can you please help?

Scott

---

### Post by tjones00 on 2011-08-24
You haven't listed what video card/driver you're using. Use whatever video driver utility to set your desired primary display to the specific monitor.

---

### Post by Scottty on 2011-08-24
My video card is a Radeon Saphire HD 5770.
The drivers disk says
Driver Ver 12-120 (7/XP/Vista only) (8.771)

When I installed Ubuntu 11.04 Desktop -386  (32 bit)
It showed a window called Additional Drivers where it said.
ATI/AMD proprietary FGLRX graphics driver and that it is not activated.

I Activated it and restarted the computer.
Once I did that only 2 monitors will work. I had the same issue when I tried
getting 3 monitors to work under (Windows XP/7) only two monitors would work

---

### Post by tjones00 on 2011-08-24
Are you running 3 displays off 2 video cards or 1? I'm assuming 1.

---

### Post by Scottty on 2011-08-24
> Are you running 3 displays off 2 video cards or 1? I'm assuming 1. 

Yes I'm running 1 video card the Saphire Radeon HD 5770

---

### Post by Maddmaxx on 2012-07-29
Amen to that brother! I'm currently running 2 HD 5770 cards, and managed to get all 3 monitors working, with no compositing, 2 1920x1080 monitors on card 1, and a 52" TV on the second card (HDMI). For the most part video performance is reasonable. I used CCC to set it up, took a LOT of playing around, but now experience the same lagging you describe when dragging windows between monitors.

If I could just have XBMC running on the TV, off the second card and the rest the way it is, I'd be okay with that, but XBMC doesn't give me the option to select one monitor, instead it spreads over all 3 monitors. So VLC it is with the video window on the TV, with the playlist undocked on monitor 2, and the file manager in monitor 1. Classic setup I've used for years. I'm too afraid to do any more at this point until someone comes up with a surefire way. Found out the hard way and through 3 reinstalls that backing up the xorg.conf file isn't enough.

I'm also getting message "Xlib: extension "RANDR" missing on display ":0.0"." when installing packages with Synaptic. Since I got this setup working reasonably acceptably I haven't been able to open the CCC as user or superuser so it's probably WAY too much to ask if compositing will work with this setup huh?

This is probably 3 threads worth of questions, but let's see where it goes. Thanks!

---

### Post by wildmanne39 on 2012-07-29
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

