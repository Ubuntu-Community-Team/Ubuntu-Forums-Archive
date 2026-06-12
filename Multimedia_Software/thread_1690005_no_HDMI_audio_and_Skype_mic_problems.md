---
title: "no HDMI audio and Skype mic problems"
date: 2011-02-17
forum: Multimedia Software
---

### Post by ADani on 2011-02-17
Hello, I'm on Kubuntu 10.04, on a Banghó laptop model: B-763XTUN. I have two sound issues with linux that are keeping me from that 100% conversion success story.

1) I dont have any HDMI audio (video works fine)
2) My mic sounds awful (chopped and imposible to understand sound) when capturing the mic with Audacity and over Skype 2.1.0.81, however it sounds fine on Windows.

```
~$ uname -a
Linux DaniPortatil 2.6.32-28-generic #55-Ubuntu SMP Mon Jan 10 21:21:01 UTC 2011 i686 GNU/Linux
```

```
~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
~$ dpkg -l | grep "alsa"
ii  alsa-base                            1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                           1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                           4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                   0.10.28-1                                       GStreamer plugin for ALSA
ii  libsdl1.2debian-alsa                 1.2.14-4ubuntu1.1                               Simple DirectMedia Layer (with X11 and ALSA 
```

```
~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC662 rev1

==> /proc/asound/card0/codec#3 <==
Codec: Nvidia MCP78 HDMI
```

Thanks in advanced for the help.

---

### Post by marin123 on 2011-02-17
1) did you set hdmi output when you connect hdmi cable to the tv? you need to go to sound preferences and choose correct output.

2) you will need to browse this forum for help with alsa issues. you might want to try alsa upgrade script or something similar. good luck :)

---

### Post by ADani on 2011-02-17
1) do you mean in Settings/System Settings/Multimedia? Yes, it's selected, when I try to test it there, it doesn't work.

2)I've been searching, the ALSA Upgrade procedure I found on member lydex signature seems a very drastic measure. On the other hand most of the threads I've seen involve modifying alsa-base.conf in a very specific way, and I'm not doing that without guidance.

thanks for the suggestions, I will keep looking into upgrading ASLA in the alsa-project.org page.

---

### Post by mikewhatever on 2011-02-17
In the Sound Preferences, make sure the hdmi output is selected.

---

### Post by ADani on 2011-02-17
@mikewhatever: Settings/System Settings/Multimedia/Device Preference Audio Output is my Nvidia HDMI card. Like I said, when I test it with the "Test" button, nothing happens.

Edit: I tried some of the things from other posts. I installed these packages from the ubuntu-audio-deb/ppa repository:
linux-headers-2.6.32-28-generic-pae (version 2.6.32-28.55) will be installed
linux-headers-alsa-driver-2.6.32-28-generic (version 2.6.32-28.201102161600) will be installed
linux-headers-alsa-driver-2.6.32-28-generic-pae (version 2.6.32-28.201102161600) will be installed

I also added the "options snd-hda-intel model= " line in alsa-base.conf and went over the list for ALC662. Most of them made my mic sound just as bad or worse, except for the 3 dell and samsung options that resulted in a better quality of sound over a very bad background noise and in mono.
So no luck there.

---

### Post by ADani on 2011-02-24
bumpity

---

### Post by inobe on 2011-02-24
here's what i know, kde kmix does a better job managing sound.

i had issues with pulse audio, my mic digital audio refused to work, most of the problem was pulse hiding the mixer controls.


i removed pulse and restarted, kde asked a question via a dialog if it could manage my sound, i selected yes.

low and behold, everything was muted, all my mixer controls were present.

i have kde 4.6 on 10.10


remember to take note of what gets removed, you may need them again if things head south.

---

### Post by ADani on 2011-02-24
Thanks but that is not my case, kubuntu 10.04 doesn't come with pulseaudio and I did't installed it, I have ALSA only and nothing is muted on alsamixer or kmix (wich, as far a I know, is only a visualization of alsamixer).

---

### Post by inobe on 2011-02-24
> **ADani said:**
> Thanks but that is not my case, kubuntu 10.04 doesn't come with pulseaudio and I did't installed it, I have ALSA only and nothing is muted on alsamixer or kmix (wich, as far a I know, is only a visualization of alsamixer).

things i would seriously try.

get latest stable release and test, test on a flash drive if you must keep 10.04 LTS, maybe pulse will FIX the issues or the latest version of kde?

**you can only do this on 10.10** [http://www.kubuntu.org/news/kde-sc-4.6](http://www.kubuntu.org/news/kde-sc-4.6)

look for the comprehensive sound guides in the forum, usually pinned.

have a look at the troubleshooting section of the ubuntu docs.'
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

search forum with keyword 'hdmi'

i hope one of my suggestions help.

---

### Post by ADani on 2011-02-27
Thanks for the input inobe. I am currently trying the liveDVD w/USB persistence method (because I've just found out my laptop doesn't support USB boot), and I've successfully solved the mic problem by returning control of the channels to ALSA without removing pulseaudio (this thread [http://kubuntuforums.net/forums/index.php?topic=3114879.0](http://kubuntuforums.net/forums/index.php?topic=3114879.0) by user Mrs_Angel_D).

However, new problems arise with Kubuntu 10.10, since I want to give it a thorough try before switching, I installed the Nvidia graphics card driver and upon restarting I get only the console, no graphic window.
startx gives me
FATAL: Module nvidia not found...failed to load the NVIDIA kernel module...
FATAL ERROR: no screen found

I am going to try upgrading the kernel. I'll tell you how it goes

I couldn't upgrade the kernel because my 9gb usb stick wasn't big enough.... I'm going to try to replicate the ALSA/Pulseaudio config that made mi mic work in Kubuntu 10.10 to my Kubuntu 10.04.

Update: Both mi mic problems and mi HDMI audio problems are now solved on Kubuntu 10.04. Apparently installing pulseaudio was the solution to both, doing so added new controls to unmute in KMix. Thanks to everyone for their input, specially inobe.

---

