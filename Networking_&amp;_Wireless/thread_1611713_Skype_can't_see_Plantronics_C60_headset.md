---
title: "Skype can't see Plantronics C60 headset"
date: 2010-11-02
forum: Networking &amp; Wireless
---

### Post by bill-lancaster on 2010-11-02
System>Sound> shows Plantronics headset exists and is working.

Skype sound setting does not see the headset.

Any ideas (I don't want to reinstall XP!)

---

### Post by gradinaruvasile on 2010-11-02
Skype doesnt need to see it.
It works like this:
The system uses PulseAudio sound server which in turn uses the devices from ALSA (that is the effective sound system, with drivers and all).
You connect a device, ALSA loads the drivers for it, PulseAudio makes easy to switch to it. Skype uses the default output given by PulseAudio (or ALSA if PulseAudio is not installed).

In this case you have to set up the device as the default sound output AND input (from the sound preferences menu that is accesible by right-clicking on the tray volume icon).
To make sure it will work, you have to connect the sound device, set it up as the default sound out/in device and then launch Skype.
I used bluetooth handsfree without problems with Skype.

---

### Post by bill-lancaster on 2010-11-02
Great - thanks, its working fine.

---

### Post by sembagdod on 2010-12-28
HI!, 
On "Windows XP"
I was able to choose "CS-60" from the Skype options (AS MIC and Speaker), and by doing that i was e able to listen to music or any Windows sound while others use voice chat on skype (at the same time)

On "Ubuntu 10.10" with Skype  2.1.0.81
I can choose the "CS-60" only from the "Pulse Audio Volume Control"
and when i checked Skype option it shows only "PulseAudio Server (local)" hence i can't use the PC sound if anyone was on Skype call. 

In addition i have to keep switch between "CS-60" and "Internal Audio Analog Stereo" before and after each Skype call. 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=179847&d=1293890458[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=179848&d=1293890458[/IMG]

Any one cal help?

---

