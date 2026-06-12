---
title: "MLS Live choppy video (flash)"
date: 2012-03-11
forum: Multimedia Software
---

### Post by matbluvenger on 2012-03-11
Hey all. MLS season just started today and I signed up for a service called MLS Live in which I can watch all the matches on my computer.

So today I was able to use it finally.

I got crystal clear, smooth video at their higher bitrates in small-screen mode but it got chop-choppy at full screen unless I went down to the lowest video quality setting... but then it's full of pixels.

Ubuntu 11.10 (Oneiric Ocelot) - Unity Shell
3.0Ghz Penitum 4 Socket 775
2GB DD2 memory
GeForce 8400 GS 512MB DDR2

Runs the same on Chromium or Firefox, or whether I'm on GNOME3, xfce, lxde, or OpenBox.

Is there a software fix for this or would overclocking my graphics card help?

---

### Post by lovinglinux on 2012-03-13
Most likely that your problem is due to CPU power. I had similar issues with flash content, which uses a lot of CPU cycles, when I had a Pentium 4 identical to yours. I could only solve the problem by upgrading the CPU to a dual core.

You could try installing the latest beta flash with [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/).

---

### Post by matbluvenger on 2012-03-14
Yeah I tried flash-aid... made it worse.


It's a real shame. I bought the mobo/cpu combo last month as a cheap quick replacement for a mobo that took a massive crap. It's actually the reason I started using Ubuntu!


Would overclocking make a difference or is the dual core really that much better?

---

### Post by lovinglinux on 2012-03-14
> **matbluvenger said:**
> Yeah I tried flash-aid... made it worse.


It's a real shame. I bought the mobo/cpu combo last month as a cheap quick replacement for a mobo that took a massive crap. It's actually the reason I started using Ubuntu!


Would overclocking make a difference or is the dual core really that much better?

I personally never tried overclocking my CPU, but if you are comfortable and experienced doing that, it might be a workaround. Just keep in mind P4 runs hot on normal condition, so you will need to monitor your CPU temperature more closely. In my case, when I had a P4, I was able to partially fix flash performance issues, but as soon as the CPU increased the temperature, the video would start lagging.

Just to make sure, I suppose your CPU has Hyperthreading. So, before overclocking, enable that in BIOS, if not enabled already, and you might be able to watch fullscreen.

The dual core made a big difference in my case. I was even able to watch HD flash content.

---

### Post by matbluvenger on 2012-03-14
Yeah before reading your post I tried many different frequency changes using Synchronous Overclocking between CPU and PCIE. I found the most stable and best flash-video-improvement to be at 3.46GHz. 

But I enabled hyperthreading back at the factory 3.0GHz and the improvement is equal if not better. So I'm going to try HT and a slight overclock. Just going to keep the temp under 54*C.

---

### Post by lovinglinux on 2012-03-14
> **matbluvenger said:**
> Yeah before reading your post I tried many different frequency changes using Synchronous Overclocking between CPU and PCIE. I found the most stable and best flash-video-improvement to be at 3.46GHz. 

But I enabled hyperthreading back at the factory 3.0GHz and the improvement is equal if not better. So I'm going to try HT and a slight overclock. Just going to keep the temp under 54*C.

Let me know if it works.

BTW, I just updated the flash version downloaded by Flash-Aid, because an user reported the flash download link wasn't working. Adobe removes the file from the server when they issue an update. So, you might want to try Flash-Aid again, with the latest beta flash version. If you still have Flash-Aid installed, click "Check Update" in the menu, wait for the alert about the new version, then run the Wizard again.

You could also try to disable Hardware Acceleration, since I received reports about stability issues for nVidia users. To do that visit an YouTube video, right click on it and select "Settings".

---

### Post by matbluvenger on 2012-03-15
Hardware Acceleration is definitely disabled on everything.

However, now I could probably do it! With Hyperthreading and the CPU overclocked to 3.46GHz it runs so much better in fullscreen mode. Not crystal clear like in small screen, but still massive improvements. GPU is getting no higher than 48*C (when it's working hard) and CPU no higher than 51*C. Those are values I can live with. 



.... but I'm still going to try to push it further, of course! :D

---

