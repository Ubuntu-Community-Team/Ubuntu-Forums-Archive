---
title: "Need help to investigate screen flickering and then going blank problem"
date: 2024-03-01
forum: Multimedia Software
---

### Post by swangnation on 2024-03-01
Hi guys, I'll apologise in advance if this is being posted in the wrong forum, if it is, then by all means move it to the correct one.

My problem. I have a lenovo t570 thinkpad laptop with Ubuntu 22.04.4. My screen began to flicker recently ( a few weeks ago ), so after doing some googeling i discovered that I did not have the correct graphics driver. I have a Nvidia GeForce940MX graphics card. In software updates additional drivers, the recommended driver was Nvidia Server Driver metapackage from nvidia-driver-470-server (proprietary).

After installing the above mentioned and recommended driver, all seemed well however when i use telegram, the flickering makes itself present, and i think this would have been the fourth time now that the screen has gone completely blank which forces me to power off and reboot. When i use VLC media player and i need to skip during a video, the sound turns off temporarily and then returns. These things were not happening before I installed the recommended driver.

I don't know what to look for so what is the best way to investigate this problem in order to find a solution?

---

### Post by Autodave on 2024-03-01
Hopefully someone else will back me up here, but you should be running a lot newer driver than that.  nVidia's site lists the 550 driver as the newest.  I would go to the Software Center or Synaptic and at least install the 535 driver.  They worked the bugs out of that and it seems to be rock solid now.

You may have to update your kernel to 6.1, also for the driver to function properly.

---

