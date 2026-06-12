---
title: "Suggested video card?"
date: 2006-07-26
forum: Multimedia &amp; Video
---

### Post by code-breaker on 2006-07-26
I am new to ubuntu (and linux). I have dapper installed with no problems. 

The time has come to buy a new monitor. I have found the one I want, a flat panel, but it's native resolution is 1600 x 1200, meaning my on-board video won't cut it. So, I am in the market for a good cheap (<$75) agp (up to 8x) video card that can output that resolution. Any suggestions? 

I ask because the one unsatisfying aspect of installing ubuntu was that video performance was poor with my on-board S3 unichrome chip. I did some googling, and tried to update the driver (apparently it uses a default vesa driver?), but I was unsure of what I was doing, so I decided to just live with poor performance. Now that I need a new monitor (and card), I thought it a good opportunity to get something that was known to work well (compatibility as well as performance) with linux.  

Thanks!

---

### Post by Simian on 2006-07-26
> **code-breaker said:**
> I am new to ubuntu (and linux). I have dapper installed with no problems. 

The time has come to buy a new monitor. I have found the one I want, a flat panel, but it's native resolution is 1600 x 1200, meaning my on-board video won't cut it. So, I am in the market for a good cheap (<$75) agp (up to 8x) video card that can output that resolution. Any suggestions? 

I ask because the one unsatisfying aspect of installing ubuntu was that video performance was poor with my on-board S3 unichrome chip. I did some googling, and tried to update the driver (apparently it uses a default vesa driver?), but I was unsure of what I was doing, so I decided to just live with poor performance. Now that I need a new monitor (and card), I thought it a good opportunity to get something that was known to work well (compatibility as well as performance) with linux.  

Thanks!

I wont pretend to know a lot about video cards, but I do know that Nvidia have much better drivers for Linux than ATI.

As I'm sure you know, once you have installed you new Nvidia (or ATI) card you must install the correct drivers if you want to enable 3D graphics.
```
sudo apt-get install nvidia-glx
```

and then to enable it
```
sudo nvidia-glx-config enable
```
then you need to restart X, Ctrl-Alt-backspace  (make sure you save any work first)

Good luck

---

### Post by code-breaker on 2006-07-27
Thank you Simian. I have ordered a Geforce video card, and we'll see how it goes!

---

