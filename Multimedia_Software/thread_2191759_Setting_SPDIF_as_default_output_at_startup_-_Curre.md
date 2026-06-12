---
title: "Setting S/PDIF as default output at startup - Currently always turned off"
date: 2013-12-04
forum: Multimedia Software
---

### Post by TheYetiWakes on 2013-12-04
How do I set Ubuntu to always choose SP/DIF as the default sound output at startup?  Currently its always turned off at bootup and I have to go to sound settings and turn it on each time.  

I'm running a HTPC which boots directly in XBMC.  I used to simply have a HDMI cable output to a surround amp for video/sound duties which worked fine.  However, the amp has broken and as a replacement im currently running the HDMI cable to the TV for video and optical SP/DIF to a normal stereo amp for the sound.  But when Ubuntu starts it seems to have either HDMI or analog set as the default (im not sure which) and SP/DIF digital output is always turned off.  Its a matter of having to drop back into the desktop, go into sound settings and turn on SP/DIF digital.  

I've seen various similar threads but nothing that has answered my query.  I've loaded Alsamixer and made sure SP/DIF is unmuted in there and also tried by setting the automatic mute outputs option in there to disabled but nothing changes.   I'm guessing Ubuntu is detecting the HDMI cable and giving that priority over it and muting the other ouput? Or is it simply choosing analog at startup?  Both the HDMI and the optical cable are being plugged directly into the outputs on the Motherboard - a ASUS P8H77-M PRO running intel H77 chipset and Ivybridge i3 3225 CPU.  System is Mythbuntu 13.10.

When I am in sound settings I have three options - the HDMI, the SP/DIF and the analog.  If I turn on SP/DIF sound then works fine.  Choosing analog automatically turns it off again and I have to turn it back on but that I assume is to be expected. Perhaps this is what it is doing at bootup? HDMI stays turned on all the time.  

It all works and the system is obviously capable of outputting sound over optical and video over the HDMI its just trying to get it turned on like that at bootup.

---

