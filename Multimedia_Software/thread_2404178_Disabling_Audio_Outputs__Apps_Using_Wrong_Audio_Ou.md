---
title: "Disabling Audio Outputs | Apps Using Wrong Audio Outputs"
date: 2018-10-21
forum: Multimedia Software
---

### Post by BadServo on 2018-10-21
I've installed Ubuntu 18.10 after a long period of using Windows as my daily driver OS.  I'm running into one issue though.  Audio output is positively maddening.  Currently, in the Ubuntu settings panel's Sound section, I have an HDMI output to my monitor, an audio line out to my desktop speakers, an audio output to my Oculus Rift, etc...  Generally I want only the speakers active, unless I connect a bluetooth headset.  No matter what I do, on reboot the default audio output has changed to the Rift headphones.  This is annoying, but not a huge deal.  The REAL problem is that randomly, some applications will output to the currently selected default, and some will output to another device entirely.  I can only assume that some apps are using ALSA and others using Pulse.

It seems like the simplest option would be to disable the unneeded output, but I cannot for the life of me figure out how to do it.  Any insight is appreciated.

---

### Post by nik.charles on 2018-12-20
> **BadServo said:**
> I can only assume that some apps are using ALSA and others using Pulse.

It seems like the simplest option would be to disable the unneeded output, but I cannot for the life of me figure out how to do it.  Any insight is appreciated.

Until you can confirm if your assumption is correct there is no point suggesting multiple possible solutions that may or may not help

 suggest you install the 'official' Pulseaudio mixer if you do not have it already 
Full name is 'Pulseaudio Volume Control' if you are searching in Software, or use this command:
```
sudo apt-get install pavucontrol
```

'pavucontrol --tab 1' will show all Pulseaudio playback audio streams, each audio stream will have drop-down menu to select correct playback device
'pavucontrol --tab 5' will allow you to disable any unused audio devices (use drop down-menu and select 'Off')

---

### Post by BadServo on 2018-12-20
Thanks for the help.  In my previous efforts to fix this issue, I installed pavucontrol and disabled outputs as you suggested.  Ultimately it didn't help and unwanted outputs would occasionally still become the default on reboot.  However, at some point in the past couple of weeks, the problem appears to have solved itself.  The correct "Line-Out" output has consistently bee selected when I reboot.  I haven't changed anything from a hardware perspective, so perhaps an update patched this issue away.

---

