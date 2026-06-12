---
title: "Mythbuntu 9.10 ALSA sound issues after upgrade"
date: 2009-12-17
forum: Mythbuntu
---

### Post by Verzweifler on 2009-12-17
Let me start with a success story first, before I come back to the issues I still have:
After upgrading my mythbuntu-box from 9.04 to 9.10 sound was dead. I soon realized that this was no unusual issue; however, the hints I found did not help... 
I determined that my sound card (an onboard device) was properly detected by the system ```
cat /proc/asound/cards
 1 [               ]: USB-Audio - PnP Audio Device        
                      PnP Audio Device         at usb-0000:00:02.1-4, full speed

cat /proc/asound/modules
 1 snd_usb_audio
```but was assigned index 1 instead of 0 as I would expect for the only sound device available at all. A brief look at /etc/modprobe.d/alsa-base.conf revealed the issue: 
```
options snd-usb-audio index=-2
``` actually prevented my soundcard from being the default device used by alsa, so I changed the index to 0 and all was fine... Almost...

Now comes the issue part:

In the frontend running on the very same machine, I had sound but now there is no way to control it. alsamixer works fine (it didn't work before tweaking around), but within mythtv, the OSD sound-bar reacts when doing volume-up/volume-down, but the volume itself stays unchanged (at a high level). Also muting does not work although the OSD tells me "mute"...

I have no idea how to get this solved. In the mythtv configuration, all sound-related values are set to alsa:default, which was the working default in mythbuntu 9.04...

Any help is appreciated.

---

### Post by ender8282 on 2009-12-24
I had a similar problem.  I upgraded fro Mythbuntu 9.04 x86_64 to 9.10.  After the upgrade Mythbuntu gave no sound but I could hear it while running the hulu player.  My fix was to start myth frontend --> Utilities/Setup --> Setup --> General.  From here I ran through a bunch of setup options until I found sound options.  I pretty much set everything I could to ie958 and sound was back.  Wander though that and see if you can get stuff working.  Post back and I can try to give you better details.

---

