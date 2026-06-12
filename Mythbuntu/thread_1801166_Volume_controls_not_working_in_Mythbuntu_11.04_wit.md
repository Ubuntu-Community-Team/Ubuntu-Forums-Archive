---
title: "Volume controls not working in Mythbuntu 11.04 with Media Center Remote Control"
date: 2011-07-10
forum: Mythbuntu
---

### Post by PatrickD-52761 on 2011-07-10
Hello everyone,

I have two Hauppauge HVR-1600 tuners in my computer, with one USB Remote Control running them (Widows Media Center remote RC6 via lirc).  Everything seems to work normally, except that when I change the volume (either using the volume up or down buttons or the mute button) nothing happens.  On my display, it will show the volume increasing/decreasing or "Mute On"/"Mute Off". But as for the actual volume, it doesn't change at all.

I'm assuming that since the onscreen display reflects some change in volume/mute, the issue lies somewhere other than the remote and lirc.  But, I'm clueless as to where to start first. I also tried this using the "F" key (to bring up the Adjust Volume 0% box) and arrow keys to adjust the volume. There is no change in volume, regardless of what the "Adjust Volume" shows.  So, the issue lies somewhere between Mythfrontend and my Audio controls.

Also, when I close Mythfrontend and open the "Sound Preferences", my settings for the internal device don't work. I can choose Analog Stereo Output, Analog Stereo Output/Mono Input, or anything else, and when I click "Test Speakers" I don't hear any sound at all.


The computer is running Mythbuntu 11.04 (upgraded from 10.10) and uses the built-in soundcard on the motherboard (board is a Biostar M7-VIG).  The volume worked prior to upgrading from 10.10 to 11.04.

Any suggestions and help is greatly appreciated.

Have a great week:)
Patrick.

---

### Post by PatrickD-52761 on 2011-07-10
A little more information. The Sound card is a VIA V8235 according to cat /proc/asound/devices. It's using the latest ALSA drivers that were available when I installed Mythbuntu. (the V82xx and snd82xx drivers according to DMESG). I can post details as required.

Have a great weekend/week. :)
Patrick.

---

