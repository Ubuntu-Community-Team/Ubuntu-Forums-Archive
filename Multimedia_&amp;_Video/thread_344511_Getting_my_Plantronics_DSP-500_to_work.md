---
title: "Getting my Plantronics DSP-500 to work"
date: 2007-01-23
forum: Multimedia &amp; Video
---

### Post by richbl on 2007-01-23
Hello all,

Well, after spending some time trying to figure out how to get my Plantronics DSP-500 USB headset to work, I found a solution (at least it appears to be a fix).

**The problem**: my motherboard has onboard audio, which I disabled in BIOS. I use a USB headset exclusively for audio, so no need for the onboard audio. After installing Ubuntu (6.10), I found that my headset would not play system sounds (though it played streamed audio just fine). 

When attempting to track down the problem, many threads suggested running *alsamixer*. However, whenever I attempted to run that command, it generated the following error message:

function snd_ctl_open failed for default: No such device

**The solution**: the solution (at least for me) was to edit the file /etc/modprobe.d/alsa-base. In that file, near the bottom, I noticed what appeared to be some hacks for preventing "abnormal" drivers from grabbing index 0. Well, my driver was listed there (snd-usb-audio), and it certainly was acting abnormally. BUT, in my case (not sure what other cases there might be), I WANTED index 0 (since this headset was my only device).

So... I commented out the line like so:

# options snd-usb-audio index=-2

After a reboot, I have system sounds. And, I can now successfully run alsamixer. And so, at the moment, all appears to be well.

Hope this helps.

rich

---

### Post by hppyfngy on 2007-02-18
I have a similar problem but your solution did not work for me.  I have onboard sound, which I may or may not use (it is enabled in bios.)  

I also have a Plantronics SP500 USB.  It is recognized in the device manager, and oddly enough it will even control my system volume (although it will not mute it.)  But I have no sound out of it and it doesn't show up in the alsa manager.  

I did as you suggested and still have the same problem, anyone else have a solution for getting usb headset to work?

---

### Post by hppyfngy on 2007-02-19
[http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_change_default_soundcard](http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_change_default_soundcard)


This worked for me to set my headset as default device, but I have to use alsamixer to control volume...

---

### Post by John Hughes on 2007-06-22
[http://ubuntuforums.org/showthread.php?t=480930](http://ubuntuforums.org/showthread.php?t=480930)

I have posted this as a solution!!!

---

