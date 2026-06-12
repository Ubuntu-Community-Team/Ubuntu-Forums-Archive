---
title: "Headphones not working on Ubuntu 11.04 64 bit"
date: 2011-08-04
forum: Multimedia Software
---

### Post by tm2383 on 2011-08-04
Hi,
I am having trouble getting my headphones to work on my 64 bit Ubuntu 11.04 distro. When the headphones are plugged in, sound continues to come through the normal speakers.
I have read other posts on this topic, but cannot solve the problem.

I used the alsa info script using this command.

```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
```The output is displayed at:

```
 http://www.alsa-project.org/db/?f=e17dca5c059847d3a84b9f10a174e4dfc090472c 
```Is there anything that I can do to correct my problem, based on this info?

Thanks,

Tim

---

### Post by CowboyCoffee on 2011-08-04
I keep having the same problem. I tried this: pulseaudio --kill && pulseaudio --start but it didn't help. Can't get them working without a restart.

---

### Post by Furball588 on 2011-08-04
So to confirm....when you say normal speakers, you're talking about something that's fed through your HDMI?

Off hand, I'd think you'd just need to select your output source (right click on the speaker applet).

---

### Post by tm2383 on 2011-08-05
Just the normal speakers on the laptop. On Windows, I just plug in the headphones and they work. Everything gets so complicated with linux :-)

tim

---

### Post by tm2383 on 2011-08-07
Any ideas anyone? Linux is getting so buggy these days that I'm just thinking of repartitioning my drive and going back to Windows. Windows isn't perfect, but its surely better than this :-(

---

### Post by CowboyCoffee on 2011-08-14
Someone has to have an answer, or at the very least, an idea?

---

