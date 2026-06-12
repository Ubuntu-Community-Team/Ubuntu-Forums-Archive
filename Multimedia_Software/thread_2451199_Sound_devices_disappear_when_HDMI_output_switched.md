---
title: "Sound devices disappear when HDMI output switched"
date: 2020-09-29
forum: Multimedia Software
---

### Post by jfaberna on 2020-09-29
I have an older PC with an Nvidia GT1030 video card and it's connected to a UHD TV through a 5x1 HDMI 2.0 switch.

With everything working if I switch the TV to another HDMI input using the 5x1 switch, when I switch back, the video comes back fine but the audio now is set to /dev/null and there are no other choices.  

To fix this I have to reboot and then the sound is back to the Nvidia GT1030 HDMI port just like the video.

Anyway to force the sound to reconnect just like the video??

BTW, when audio disappears for applications that use the default audio devices, a program like mythfrontend that specifies the audio device within the application does work.

---

### Post by jfaberna on 2020-10-08
what I have found is that if I look at the audio mixer it will report the Dummy device being the current output device.  If I go to the mixer configuration tab, all the profiles are unavailable. If I select the right HDMI profile anyway it takes a few seconds but the Unavailable tag goes away and then the sound works until I switch the HDMI for the TV away from the PC.

There has to be a way to force the audio back active just like the Video does when the HDMI is reconnected.

---

