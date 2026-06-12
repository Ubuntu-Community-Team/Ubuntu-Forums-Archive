---
title: "hvr950 jaunty no sound"
date: 2009-05-13
forum: Multimedia Software
---

### Post by maddocks on 2009-05-13
Im trying to use the Hauppauge WinTV HVR 950 on jaunty using the drivers built into the kernel. I extracted the firmware rebooted and the card is recognised and i can use mythtv tvtime xawtv etc. and the video works fine but no audio. ive found many sites that say to use the following command to fix (my setup has the tuners audio on dsp1)

 sox -r 48000 -w -c 2 -t ossdsp /dev/dsp1 -t ossdsp /dev/dsp

but that command fails because it doesnt like the -w switch. heres the error;
sox: invalid option -- w

Any ideas? Ive also tried editing /etc/modprobe.d/alsa-base.conf and changed options snd-usb-audio index=-2 to options snd-usb-audio index=1 to no avail.

---

### Post by ed325i on 2009-05-14
I need help from you.  :)

I have a HVR-850, which is almost the same as your HVR-950.  How did you install any of the drivers, including the firmware?  I am a Linux newbie.  Thanks!

---

### Post by loudness on 2009-05-15
> **maddocks said:**
> Im trying to use the Hauppauge WinTV HVR 950 on jaunty using the drivers built into the kernel. I extracted the firmware rebooted and the card is recognised and i can use mythtv tvtime xawtv etc. and the video works fine but no audio. ive found many sites that say to use the following command to fix (my setup has the tuners audio on dsp1)

 sox -r 48000 -w -c 2 -t ossdsp /dev/dsp1 -t ossdsp /dev/dsp

but that command fails because it doesnt like the -w switch. heres the error;
sox: invalid option -- w

Any ideas? 
Read [the FAQ]("http://sox.sourceforge.net/Docs/FAQ"), Luke

---

### Post by maddocks on 2009-06-02
be carefull up until jaunty you needed to download and compile the mercurial (?SPELLING?) drivers, which required a different firmware. Jaunty has a built-in kernel module wich just requires you to download and extract the firmware to /lib/firmware. I caint remember where i got the firmware but i believe i needed and subsequently used a python app to extract the firmware.Ironically i had the same problem using the custom compiled modules as the one now built-in. I do remember that the "old school" method with mercurial used to wreak havoc with any other v4l2 devices like webcams that used the uvcvideo module. I would love to find out why the sox hack doesnt work for me,,hint hint,,,if anybody is still reading this post,,hint hint

---

