---
title: "Audio good in TV but not MythWeb"
date: 2012-09-03
forum: Mythbuntu
---

### Post by johnvic on 2012-09-03
As the Title says, I can hear sound watching TV. Also, I can hear sound when I watch internet videos in MythTV. But if I watch videos in a news feed or in the web browser I get no audio. Also, if I quit mythfrontend and watch a video in the chromium web browser I get no audio. However, if I use VLC player to directly watch my hdhomerun stream I get audio. I also have no sound setting on the kfce toolbar or in any of the menus. 

So audio is good in mythTV, VLC from desktop and mythnetvision.

Audio is no good in Chromium web browser and mythweb and I have no settings on the desktop to adjust audio. Alsamixer has the outputs at 100%.

I am running a mythbuntu combined frontend and backend system. The version is 12.04.1 LTS. The desktop is kfce 4.8. The PC is an AMD 64 X2 4400. The mobo is Asus A8V with 2 gigs of RAM.

Any suggestions?

---

### Post by johnvic on 2012-09-04
I forgot to mention. I am using SPDIF audio on my mobo. Also, when I say I can hear sound watching TV I mean WatchTV in MythTV. 

I am not sure if this problem existed in 11.10. I did not do an upgrade from 11.10. I did a fresh install.

Here is my result when I run aplay -l


**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by nickrout on 2012-09-04
You probably need to set your default audio device to the spdif output. You can do this via /etc/asound.conf

---

### Post by johnvic on 2012-09-04
> **nickrout said:**
> You probably need to set your default audio device to the spdif output. You can do this via /etc/asound.conf

I don't see asound.conf in the /etc directory.

---

### Post by nickrout on 2012-09-05
> **johnvic said:**
> I don't see asound.conf in the /etc directory.No, you need to write one.

---

### Post by johnvic on 2012-09-07
Thanks for pointing the way Nick. I did some googling and messing about and it now works! I have audio on tv through mythtv, mythbrowser and internet tv, as well as regular web browsing. I also got help from the following web page:

[http://www.mythtv.org/wiki/Configuring_Digital_Sound_with_AC3_and_SPDIF]("http://www.mythtv.org/wiki/Configuring_Digital_Sound_with_AC3_and_SPDIF")

Here is what I wrote in my /etc/asound.conf file:


pcm.!default {
type plug
slave {
pcm "spdif"
rate 48000
format S16_LE
}
}


I need to test it with sports or and action movie to make sure I have surround. But I am 90% there at least. Thanks again!

---

### Post by nickrout on 2012-09-07
> **johnvic said:**
> Thanks for pointing the way Nick. I did some googling and messing about and it now works! I have audio on tv through mythtv, mythbrowser and internet tv, as well as regular web browsing. I also got help from the following web page:

[http://www.mythtv.org/wiki/Configuring_Digital_Sound_with_AC3_and_SPDIF]("http://www.mythtv.org/wiki/Configuring_Digital_Sound_with_AC3_and_SPDIF")

Here is what I wrote in my /etc/asound.conf file:


pcm.!default {
type plug
slave {
pcm "spdif"
rate 48000
format S16_LE
}
}


I need to test it with sports or and action movie to make sure I have surround. But I am 90% there at least. Thanks again!

Sorry I couldn't have written that for you, but I didn't have time myself to trawl through the many posts and web pages on this topic. Glad my pointer enabled you to find it for yourself.

I love it when I learn something new, sounds like you are prepared to search and learn too!

Personally my frontends run only mythfrontend and xbmc, so I don't actually have to cope with this myself, which is why I couldn't produce a suitable file from my own system.

---

