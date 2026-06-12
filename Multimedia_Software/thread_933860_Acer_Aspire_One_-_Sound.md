---
title: "Acer Aspire One - Sound"
date: 2008-09-29
forum: Multimedia Software
---

### Post by Hawk__0 on 2008-09-29
Hello, I just bought an acer aspire one and i installed ubuntu on it yesterday.  Sound WAS working yesterday from a fresh install.  Then I followed this WONDERFUL guide here: [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

Everything is great, except now I have no functioning sound.  I believe it may be my own doing as I think I ran this chunk of code in the audio area (Rebuilding alsa):
```
sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa
sudo alsa force-unload
sudo depmod -ae
sudo modprobe snd-hda-intel
```

But no matter what no sound will play at all! I tried even opening the mixer and changing audio devices and sound levels and all to no avail.

Please help me

EDIT: SOLVED! I'm simple, all you have to do is this part:

> Now we need to make a choice. To have the internal MIC non-functional (external works), but sound working after suspend and resume, we edit /etc/modprobe.d/alsa-base (sudo gedit /etc/modprobe.d/alsa-base) and add the following line to the bottom:

options snd-hda-intel model=toshiba

---

### Post by greywolf79 on 2010-06-13
I am having a similar issue to this problem.

First about what was done. I installed the ubuntu netbook remix from the ubuntu website  about a month ago (I think it said the version was 9.10 - but I am still very new to linux). The system is an Acer AspireOne D250 model. It installed fine, everything seemed to work fine. Then I decided I wanted to do webcam conferance calls and found that the mic does not work and the webcam (built in) was only working in the Cheese program. I then went to the below website and followed its directions...

[https://help.ubuntu.com/community/AspireOneAOD250?action=show&redirect=AspireOne%2FAOD250#Fixing%20the%20microphone](https://help.ubuntu.com/community/AspireOneAOD250?action=show&redirect=AspireOne%2FAOD250#Fixing%20the%20microphone)

The result is now NO sound at all, does not recognize the sound card any longer at all, and the webcam no longer functions (even in cheese). So I need to get the sound and webcam working, and hopefully get it all to work on skype so I can make my calls (need webcam and mic and speakers all functioning). Please help...

GreyWolf79

---

### Post by stacych on 2010-06-26
Am a noob so this may not be helpful addition, but I wanted to note I also installed Ubuntu 10.04 Netbook Remix on Acer Aspire 1 D250, and cannot listen to streaming radio on cbc.ca site, or watch the streaming video.

I also couldn't set up the wireless until I did a final install (I was using the USB drive to try it and couldn't get the wireless working) and then could install the drivers easily with a wired connection just using the driver updates automatically suggested.

UPDATE:

I had partial success -- installed Adobe Flash Plugin 10 and Gnash SWF movie player and can now watch video on CBC. Watch the story of stuff, the visual was choppy, the sound was good.

Was not able to view an AVI file in the movie player app.

---

