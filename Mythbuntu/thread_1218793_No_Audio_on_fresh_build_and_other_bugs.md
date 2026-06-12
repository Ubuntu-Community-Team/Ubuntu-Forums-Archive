---
title: "No Audio on fresh build and other bugs"
date: 2009-07-21
forum: Mythbuntu
---

### Post by trevs.bronco on 2009-07-21
I have a freshly built frontend only machine with no audio output in myth or from the desktop. I have adjusted all the volume levels to max on the alsamixer and with the mic and line in volumes up I can get static when my screen goes blank......

....yes this is one of the other bugs, if I open a terminal the screen will go blank every few seconds to a few minute, for a few seconds. This is only through the analog out, not through the HDMI, which is what I really need to have working. 

The build of the machine is based on the Zotac IONITX a-u motherboard with an atom 330 dual core processor and the ION grapgics card. 

On my backend machine I had the same no sound issue and I was able to cure it by down grading the nvidia drivers from 180 to 173. I tried that on this machine without success. The Nvidia website recomended the 185.18.14 driver for my setup so that is what I currently have installed. The install of this driver was not easy, the ussual way of installing it by selecting it in "proprietary drivers" in the MCC did not work as there were no drivers listed there. I tried an application called envyNG, buit it did not list the correct drivers in its available download list.

this is what I get from the frontend log when I try to watch tv.
```

2009-07-20 22:44:35.721 TV: Attempting to change from None to WatchingLiveTV
2009-07-20 22:44:35.729 Using protocol version 40
2009-07-20 22:44:37.637 DPMS Deactivated 
2009-07-20 22:44:38.814 AFD: Opened codec 0x11013b0, id(MPEG2VIDEO) type(Video)
2009-07-20 22:44:38.814 AFD: codec MP2 has 2 channels
2009-07-20 22:44:38.814 AFD: Opened codec 0x1102920, id(MP2) type(Audio)
2009-07-20 22:44:39.123 Opening audio device 'default'. ch 2(2) sr 48000
2009-07-20 22:44:39.123 Opening ALSA audio device 'default'.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL /dev/mixer
2009-07-20 22:44:39.161 AudioOutput Warning: Mixer attach error -2: No such file or directory
            Check Mixer Name in Setup: '/dev/mixer'
2009-07-20 22:44:39.465 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-07-20 22:44:39.555 OSD Theme Dimensions W: 640 H: 480
2009-07-20 22:44:40.174 Realtime priority would require SUID as root.
2009-07-20 22:44:40.174 TV: Changing from None to WatchingLiveTV
2009-07-20 22:44:40.278 Video timing method: USleep with busy wait
2009-07-20 22:45:22.258 TV: Attempting to change from WatchingLiveTV to None
2009-07-20 22:45:22.707 TV: Changing from WatchingLiveTV to None
2009-07-20 22:45:22.759 DPMS Reactivated.
2009-07-20 22:45:25.689 Deleting UPnP client...
```So, how do I check the Mixer name in '/dev/mixer' and what should it be and how do I correct it?

Thanks,

Trev

---

