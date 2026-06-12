---
title: "GeForce GT530 HDMI out isuues"
date: 2012-04-23
forum: Multimedia Software
---

### Post by wa1d0rf on 2012-04-23
I'm running Ubuntu 11.10 with Unity display.  The HDMI connected desktop doesn't fit on the screen properly no matter how I try to adjust it.  The screen res is not set to the exact size (based on the Sony TV manual) but it is close.  It seems the top system tray is off the screen at the top and most of the Unity menu is off the screen on the left.

I installed this new ASUS GeForce GT 530 (silent) in my system and hooked up my Sony LCD TV via the HDMI port.  The desktop fits correctly if I connect via the VGA port however. I have installed the latest NVIDIA drivers and the Nvidia settings app says it is in use.  

The sound doesn't work either but I've read here how to fix that (separate issue).

Can anyone  give me some suggestions on how to get the desktop resolution setup correctly?

---

### Post by jawilljr on 2012-04-23
Your TV is doing what is called overscanning. You didn't give the model number of your TV, but [this](http://www.ehow.com/how_5877286_adjust-overscan-sony-lcd-tv.html) and [this](http://forums.whirlpool.net.au/archive/1113758)

Hope it helps.

Jerry

---

### Post by wa1d0rf on 2012-04-23
thanks for those links, very interesting indeed!  My Sony TV is a Bravia model KDL-40S2010.  I tried it with the DVI-HDMI adapter between the video card and the HDMI cable and the screen looked the same after I booted up.  I tried the TV menu (settings / picture) but the "picture mode" gives me choices like "Vivid", "standard" and "custom".  I changed it to "custom" and I had more options available but nothing that says "full pixel" or that would give me any correct to the over-scan situation.  The "wide mode" option was greyed out for some reason.

---

### Post by papibe on 2012-04-23
Hi wa1d0rf.

I have a Sony Bravia. In my case the menu to correct overscan is this:
```

Screen -> Wide Mode     -> Full
       -> Disaplay Area -> Full Pixel
```
I hope that helps.
Regards.

---

### Post by wa1d0rf on 2012-04-23
thanks for that papibe, but my settings/screen/wide mode gives me normal/full/zoom/wide zoom options and the display area gives me normal/-1/-2 options. This model is about 5-6 years old, maybe they changed the settings options since then?  Also, as I stated before, I don't get access to all features when I'm attached to the PC as opposed to a regular TV input.

---

### Post by papibe on 2012-04-23
Sorry to hear that, but there may be a solution.

The proprietary Nvidia driver has an option to adjust overscan. Take a look at [this]("http://smartsoftwarefactory.blogspot.com/2011/01/correct-tv-overscan-using-ubuntu-nvidia.html") article to learn how to do it.

Regards.

---

### Post by wa1d0rf on 2012-04-23
I thought this solved the problems I was having but when I tried to fix the audio issues (no sound with HDMI), I rebooted the system and it messed up all the settings for the video.  It says it can't read the settings.  I'm trying to get back to it so I can get more details.

---

