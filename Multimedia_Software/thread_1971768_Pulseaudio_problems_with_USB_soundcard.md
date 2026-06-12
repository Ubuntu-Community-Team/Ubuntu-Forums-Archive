---
title: "Pulseaudio problems with USB soundcard"
date: 2012-05-02
forum: Multimedia Software
---

### Post by tristan on 2012-05-02
One of the few really annoying problems I've encountered with 12.04 is sound. I'm running 12.04 on my Acer netbook and it works beautifully. Obviously the netbook has crappy little speakers so I prefer to listen to music via an external USB sound device (either a Logitech Z305 or a Topping TP30 integrated USB DAC/Tripath amp).

If I turn the netbook off, plug in the USB sound device, and boot, then Sound Settings has no problem recognising the device and allows me to switch output to it (either analog or digital).

However if the netbook is already running when I plug in the USB sound device, then I simply cannot switch output. The USB device appears in the list of outputs, but clicking on it has no effect. I had far fewer problems in this regard with earlier versions of Ubuntu.

This is pretty annoying since it means if I want to listen to decent quality sound I don't have the option of simply connecting my running computer to  USB device, but have to reboot.

Does anyone know the best way to deal with this? 

TIA

---

### Post by gnuman on 2012-05-05
I am also having many problems with sound in 12.04, but I'm attempting more than just listening via usb audio interface.  I'm attempting to get a decent recording setup and have tried a LOT in the past week ( realtime, disabling pulseaudio, changing config files ... ).  The are so many variables in my setup, but if I find something that may help others, I will post what I learned.

Good luck.

---

### Post by yoyoyojomo on 2012-05-07
A workaround that works for me is to run "pulseaudio -k" after plugging in the USB sound adapter. Still inconvenient, but better than rebooting.

---

### Post by tristan on 2012-05-08
> **yoyoyojomo said:**
> A workaround that works for me is to run "pulseaudio -k" after plugging in the USB sound adapter. Still inconvenient, but better than rebooting.

Many thanks for this, I will give it a try.

---

### Post by gnuman on 2012-05-08
Saying anything about Pulseaudio can cause a flame war, it seems, but all I care about is being able to use some of the great tools that have been with Linux for a while now.  The average Ubuntu user will probably never know about the struggles faced by users that want to use a USB audio interface for recording (using LMMS, Ardour, Hydrogen, and all the great programs like Alsa Modular Synth).  To make things worse, I'm using an iMac and dual booting Ubuntu with OSX.

For a while I tried removing pulseaudio and trying to work without it.  That can be quite tricky, and I had little success trying many approaches (Ubuntu Studio 12.04, realtime kernel, etc).  

I'm now pretty happy with my current setup.  I did a fresh install of 12.04 Ubuntu and tried very hard to work with pulseaudio and make everything get along well enough for recording purposes.  Didn't work.  I ended up removing pulseaudio and doing a LOT of tweaking to get a working recording setup.  I'm NOT using the realtime kernel, but what I have now is pretty workable.  Heck, even OSX (which people say is great for easy audio work) shows some unpredictable behavior when recording audio.  I would say I have an Ubuntu setup now that is just as good as what I have on OSX.

Basically I fire up Jack, using Qjackctl, and then start up the programs I'll be using.  I may, for instance, start up Rakarrack or a software synth like Yoshimi, and then either Audacity or a DAW.  I don't have to put the settings in Jack for really low latency--it seems that the USB audio interface makes a lot of that un-necessary.  So, although Jack says the latency will be at a level that I wouldn't normally use, the result is that I have no complaints about latency.

But I'm willing to live without sound for almost anything else.  Not that I can't make it work for web browsing, etc--those are just lower priorities for me at this time.  

BTW, using "pulseaudio -k" would be great if it worked in my situation.  The problem was that it respawned and the whole mess was an unstable ... mess.  I tried keeping it around (like surpressing any re-spawn attempts), but in the end I got much further just removing it.

---

