---
title: "Hard Crash Problem with Intel i915 Video"
date: 2006-02-04
forum: Multimedia &amp; Video
---

### Post by K0LO on 2006-02-04
This one has been driving me crazy for 2 months now. I have a Shuttle SD11G5 system using a Pentium-M processor and containing the Intel 915GM + ICH6M chipset and using the Intel Integrated Graphics Controller.

For reference, I'm running Kubuntu 5.10, kernel 2.6.12-10-386, and KDE 3.4.3. Accelerated video in 1600 x 1200 mode looks great and seems as fast as it should be (glxgears > 1000 fps).

However, I get hard crashes occasionally where the machine will just lock up. In this state it won't respond to the keyboard or mouse, the CUPS server and SAMBA servers die, you can't ping the machine over the network, and on the monitor you can see the video display frozen but there is some random pixel motion across the screen, especially overtop of Superkaramba objects. In this state all that you can do is press the reset button and start over.

Unfortunately there is no information in any of the logs. All that you can see is normal operation up until the time of the crash. For example, you can tell what time it crashed by looking at the /var/log/messages file and seeing an entry every 20 minutes when it's up, and stopping when the crash occurs. Because of what I have observed, and from reading comments from others on this forum who are having hard crash problems with their ATI video cards, I suspect that the crash has something to do with the video subsystem, especially since this video shares memory with the main system RAM.

Here are some additional observations:
1. If I turn on several Superkaramba objects that continually write to the video display and just leave the machine running, it will crash within 24 hours.
2. If I turn off the Superkaramba objects and leave up the Amarok player (with a scrolling marquee at the top of the display) it will stay up for a few days before it crashes.
3. If I just leave a static terminal window on the screen, it will go for a long time (I stopped after 2 weeks so that I could continue to troubleshoot). 

Here are some things I've done to troubleshoot:
1. Try the Superkaramba objects one at a time (Liquid Weather, Cynapses, dBKalendar). Doesn't matter -- if only one object is displayed on-screen it will eventually crash.
2. Turned off "Use Fast Image Scaling" on the Superkaramba objects -- still crashes.
3. Start Superkaramba but don't display any objects -- fine; no crashes.
4. Upgrade Superkaramba to the latest version 0.37, compiled from source -- still crashes.
5. Since I suspect the video subsystem, and Intel i915 video uses a shared memory architecture, I tried going into the motherboard's BIOS and disabling Dynamic Video Memory Technology (DVMT), instead setting the video memory to a fixed 128 MB and leaving the rest of the 1 GB of memory to Linux. This configuration ran successfully for a few days but eventually crashed.

After searching around, I don't see too many other people reporting crashes with Superkaramba. Since most people use the Intel Integrated Graphics on a laptop, and they don't leave their laptops on continually, I'm not surprised to see very few reports of crashes.

Unfortunately for me, this is a desktop machine that I'd like to leave up 24/7 as a local print/file server, so I need to fix this.

Is anyone else having similar problems with the i915 video? Can you suggest anything else that I could try?

**Edit 3/7/2006** Solved, finally! It was a hardware problem (memory). Had to leave memtest86 running for >40 hours to get the problem to show up; it was **very** intermittent.

---

