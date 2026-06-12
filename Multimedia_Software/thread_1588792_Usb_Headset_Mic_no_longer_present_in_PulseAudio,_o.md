---
title: "Usb Headset Mic no longer present in PulseAudio, ok in alsa though"
date: 2010-10-05
forum: Multimedia Software
---

### Post by JackSchnippes on 2010-10-05
Hello Forum members,


yet again I am in need for some hints :)
until a few days ago I had no problems whatsoever using my generic usb headset with ubuntu and pulseaudio. but now in the "sound preferences" dialog, I only see "Audio Adapter Analog Stereo" in the "Output" tab. I used to have a similar entry in the "Input" tab, but it's not there anymore. So mic on headset doesn't work anymore, since I can't select it. Everything seems okay in alsa, though (headset is  **card 1**):

```
arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
**card 1**: default [C-Media USB Headphone Set  ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: Pro [FastTrack Pro], device 1: USB Audio [USB Audio #1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```I have to mention that I did some tweaking on PulseAudio to work around [a bug to get my M-Audio Fast Track Pro]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/569932") going. But I only had to edit a line in /usr/share/pulseaudio/alsa-mixer/profile-sets/maudio-fasttrack-pro.conf so I don't think this should affect the USB headset. Maybe I screwed somewhere else. I'm sorry if this turns out to be my fault!

I got 2 attachments but they were too big for this forum, so here are the links:
[verbose PulseAudio log]("http://pastebin.com/3v3nL78e")
[alsa info]("http://pastebin.com/dAcgm5ZZ")

thank you for helping!

---

### Post by JackSchnippes on 2010-10-05
Ahh! I got it :)

Seems like I changed the PROFILE in the HARDWARE tab from "Analog Stereo Output + Analog Mono Input" to "Analog Stereo Output"! :P

I switched back and now it works again! Doooh! :P

---

