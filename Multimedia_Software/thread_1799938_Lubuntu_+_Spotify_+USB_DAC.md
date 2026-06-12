---
title: "Lubuntu + Spotify +USB DAC"
date: 2011-07-08
forum: Multimedia Software
---

### Post by Moblin on 2011-07-08
Hi everyone
I'm having a hard time figuring out how to use Spotify with my USB DAC. In MOC, Audacious etc it works great because I can configure what soundcard to use. Spotify only uses my laptops internal soundcard. Anybody have an idea how I can solve this?

ps: I'm using a Lenovo T60p

Thanks

---

### Post by Moblin on 2011-07-08
Never mind. I figured it out :D

---

### Post by timrichardson on 2012-12-13
this is an old thread, but prominent in google searches for ubuntu usb external dac. I just got my dragonfly connected to a dell running xubuntu 12.10. 
To get spotify audio going to the DAC, I blacklisted my internal sound card. I found the module name by searching through lsmod and then adding it /etc/modprobe.d/blacklist.conf
after rebooting, the dragon fly was the only audio on the computer and spotify went there. Initially it was silent although the volume control panel showed activity. I had to nudge the volume slider fractionally above the default setting. 

The sound quality is astounding under Spotify high quality streaming.

---

