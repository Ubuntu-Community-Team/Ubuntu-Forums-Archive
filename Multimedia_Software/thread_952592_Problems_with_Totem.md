---
title: "Problems with Totem"
date: 2008-10-19
forum: Multimedia Software
---

### Post by CGS_Saltire on 2008-10-19
Hi Guys!
Forgive me if I am posting in the wrong forum but since this concerns Totem (both versions) and for a while concerned Mplayer I thought I would ask here...

I am also still learning to cope with Linux so please be patient...

When I first installed Hardy and the GStreamers required to run it Totem was working fine. I don't know what caused it to happen but suddenly one day after booting Ubuntu I tried to play a video and noticed that while it played the video the result was loss of colour to something more like a monochrome image. At first I thought that the clip was degraded having not long downloaded it then I tried to play it using MPlayer and got the same result which seemed to confirm it. I transfered the file to Windows (My system is dual boot) and discovered that it was fine. 

Further investigation in MPlayer changing the codecs didn't work until I checked the Video driver in MPlayer preferences. The corrupted/degraded format was being obtained using the xv (X11/xv) driver so I changed this to x11 X11(XImage/Shm) and with the same codecs as before fixed the problem perfectly. However Totem still has the corrupted/degraded (red show as various shades of green etc.) video format. 

My problem is I don't know how or if it is possible to change the driver Totem uses to the same setting I have in MPlayer. I use Totem quite a lot and have only reserved MPlayer for those videos that Totem doesn't seem to play so well. Not having the experience to know what code to use I could do with some help please and advice. I am assuming that the driver that Totem is using is xv! Can anyone help please!

Steve :confused:

---

### Post by kostkon on 2008-10-21
> **CGS_Saltire said:**
> Hi Guys!
Forgive me if I am posting in the wrong forum but since this concerns Totem (both versions) and for a while concerned Mplayer I thought I would ask here...

I am also still learning to cope with Linux so please be patient...

When I first installed Hardy and the GStreamers required to run it Totem was working fine. I don't know what caused it to happen but suddenly one day after booting Ubuntu I tried to play a video and noticed that while it played the video the result was loss of colour to something more like a monochrome image. At first I thought that the clip was degraded having not long downloaded it then I tried to play it using MPlayer and got the same result which seemed to confirm it. I transfered the file to Windows (My system is dual boot) and discovered that it was fine. 

Further investigation in MPlayer changing the codecs didn't work until I checked the Video driver in MPlayer preferences. The corrupted/degraded format was being obtained using the xv (X11/xv) driver so I changed this to x11 X11(XImage/Shm) and with the same codecs as before fixed the problem perfectly. However Totem still has the corrupted/degraded (red show as various shades of green etc.) video format. 

My problem is I don't know how or if it is possible to change the driver Totem uses to the same setting I have in MPlayer. I use Totem quite a lot and have only reserved MPlayer for those videos that Totem doesn't seem to play so well. Not having the experience to know what code to use I could do with some help please and advice. I am assuming that the driver that Totem is using is xv! Can anyone help please!

Steve :confused:
Yes. Open a terminal or press ALT+F2 and give:
```
gstreamer-properties
```

Select the *Video* tab, and in the *Default Output* section select the driver you want from the *Plugin* drop-down menu item.

---

### Post by mc4man on 2008-10-22
It may just be the totem bug, read here 

[http://ubuntuforums.org/showthread.php?t=869210&highlight=playback+black+white](http://ubuntuforums.org/showthread.php?t=869210&highlight=playback+black+white)

[http://ubuntuforums.org/showthread.php?t=769209](http://ubuntuforums.org/showthread.php?t=769209)

---

### Post by CGS_Saltire on 2008-10-22
Many thanks for the tips Guys! Totem is back in action in full colour! I located the problem in the driver I was using for my nVidia graphic card! Changing this plus tweaking the settings in Totem's Preferences did the job!

I noticed though that using that code I got this result from the terminal...

gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'

Despite them being unavailable it doesn't seem to have affected MPlayer or Totem which I noticed is now fine!

Steve:)

---

### Post by CGS_Saltire on 2008-10-22
Hi Guys! Just did a quick search in Synaptic for those unavailable plugins and none of them are listed! Still, everything seems fine in both Totem and MPlayer so i can't see me losing too much sleep that they aren't there!

Steve

---

### Post by kostkon on 2008-10-22
> **CGS_Saltire said:**
> Hi Guys! Just did a quick search in Synaptic for those unavailable plugins and none of them are listed! Still, everything seems fine in both Totem and MPlayer so i can't see me losing too much sleep that they aren't there!

Steve
Yes, these messages should not worry you. They are not even error messages. It just says that the *gstreamer-properties* utility can't find these audio/video drivers in your system. And indeed, you are not supposed to have them.

---

