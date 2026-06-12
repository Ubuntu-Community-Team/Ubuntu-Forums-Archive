---
title: "Calling all Acer Revo Owners"
date: 2010-02-27
forum: Multimedia Software
---

### Post by nickhopkins07 on 2010-02-27
Hi Guys,

I'm a complete Linux 'noooob' and it's very much one step forward, then one step back again at the moment, I'm getting nowhere fast, or slow.

I'm running the latest version of Ubuntu, and have upgraded the NVIDIA drivers to the latest ones from the website (not sure if that's part of the problem). I've got XBMC installed and it seems to be working, but I can't for the life of me get anything but Stereo passed over HDMI, according to my Onkyo 606 amp that is anyway.

Can anyone tell me if it's actually possible, or if they've actually managed it, to get surround sound playing over HDMI on an ACER Revo running Karmic? I ust wanna check it is actually possible before I spend any more hours of my life on it.

Thanks Guys.

---

### Post by bigspottycat on 2010-03-05
Hi there,

I'm still waiting for my HDTV so my revo is stuck on stereo sound for now anyway...but this article might help you...

[http://www.greenhughes.com/content/how-install-ubuntu-910-and-boxee-beta-acer-aspire-revo-including-64-bit-option]("http://www.greenhughes.com/content/how-install-ubuntu-910-and-boxee-beta-acer-aspire-revo-including-64-bit-option")


The bit about sound says:

> You will notice that the Revo is still being silent when you first install Ubuntu but this is easy to fix, go to System &#8594; Preferences &#8594; Sound, click on the Hardware tab. Under Profile select "Digital Stereo (HDMI) Output + Analog Stereo Input" to make sure all sound goes through the HDMI socket. If you want to use the headphone socket instead select “Analog Stereo Output". We still have to do one slight tweak though. In a terminal d enter alsamixer and you should find that “NVIDIA MCP7A HDMI” is showing as the chip. Press the right arrow until an entry named “IEC958 1” is highlighted and make sure it is not muted (it will have “MM” displayed above it). If it is press “m” to unmute it. Press Escape to leave alsamixer. If you try the sound tests under Sound &#8594; Preferences &#8594; Sound you should find that they now work. 

Good luck!

---

