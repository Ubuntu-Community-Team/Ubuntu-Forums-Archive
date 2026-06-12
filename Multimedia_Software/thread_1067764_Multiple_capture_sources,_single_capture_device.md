---
title: "Multiple capture sources, single capture device"
date: 2009-02-12
forum: Multimedia Software
---

### Post by aie93 on 2009-02-12
Hi,

I have a Toshiba laptop which is running the latest version of Intrepid and I am wondering if there is a way to get pulse to behave in a useful manner rather than it just being another useless layer on top of ALSA.

My soundcard (HDA Intel) has three capture channels, each of which can be assigned to any of four inputs (Mic, Front Mic, CD, Line).  Pulse seems to just pick up all three as one big input and does not provide the option to choose between them or alter the input.

In order for me to use my soundcard I have to open gnome-volume-control and set up the right levels for the inputs and the correct sources.  Then I have to go to pulse and set the volume again in there.  Then I can actually use it.

It is much simpler to just use ALSA and ignore pulse, although being able to choose between these inputs from the little paman applet would be a real benefit, it just can't do it.  If it wasn't for all of Ubuntu's sound hanging off pulse now I would just remove it, but I've had trouble when doing this in the past.  Although I do have trouble with it being installed too!

Any ideas anyone about how I can do this.  I believe that I have searched for solutions, but if I've chosen bad keywords please just post me a link to relevant stuff.

Many thanks.

---

### Post by markbuntu on 2009-02-12
Due to the way the alsa devs write the drivers it is up to them to make these things discoverable separately by whatever is trying to use the driver, pulseaudio or anything else. In other words, the driver must list these as separate subdevices for them to be usable in the way you want or allow the app direct access to low level driver functions which is a no no since they are in the kernel. 

Anyway, I wouldn't hold my breath for that, the devs are busy enough trying to figure out how the OEMs are configuring the chips but you can ask them at alsa.org.

If you want to find out how useful pulse is just get a usb headset and try to configure it with alsa.

---

