---
title: "no sound with nvidia in 10.10 clean install"
date: 2010-10-17
forum: Multimedia Software
---

### Post by rosiescape on 2010-10-17
Hi All,

only been into linux for about a year so I hope I'm providing everyone with enough information. I've just done a clean install of 10.10 on my all-in-one pc and I have no sound, yet the system does detect my sound card.

aplay - l
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I had a similar problem when I clean installed 9.10 a year ago, but can't remember what I did back then to fix it. I think it had to do with an issue between alsa and pulse but I do know I had the sound control icon in the panel. 

I hear the speakers make a noise as I boot and they work fine in win7 (duel-boot system). However no sound, either alerts or from media files. I also didn't have any sound running the liveCD of 10.10 or SUSE.

from lshw -c sound I get:
```
*-multimedia            
       description: Audio device
       product: MCP79 High Definition Audio
       vendor: nVidia Corporation
       physical id: 8
       bus info: pci@0000:00:08.0
       version: b1
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
       resources: irq:21 memory:f9e78000-f9e7bfff
```

I've had a read through the forum on similar issues, but they don't seem to be quite the same problem. I'm not using HDMI as the speakers are built into my system. Everything else from the install has worked fine except the sound. If you need further information, let me know.

Thanks for any and all help :KS

---

### Post by smaug42 on 2010-10-17
I've been doing some reading on this... it's possible that you may need to manually install the alsa driver from the Realtek website:

[http://www.realtek.com.tw/downloads]("http://www.realtek.com.tw/downloads/downloadsCheck.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false")

They provide a fairly recent alsa build there (from September 2010).... although, the install steps all refer to the HDA-Intel card, not an HDA-nVidia card.  And... I'd expect 10.10 to have the latest alsa build anyway.... 

Just brainstorming here... maybe someone with more experience with this card can step in here and provide some more information?

---

### Post by rosiescape on 2010-10-17
Thanks for the suggestion.

I went to the site and downloaded and installed the driver. Unfortunately, it hasn't resolved the problem. Instead, my system doesn't recognise any soundcard at all now.

Will keep tinkering with this. Hope there are some other suggestions out there.  :confused:

---

### Post by xzero1 on 2010-10-19
I have an MSI Windtop AE2220 AIO pc that appears to have a similar problem -- no sound, though the driver is loaded and running. It seems the trick might be to get the correct configuration for the hd-audio (intel-hda). This is explained in the /usr/share/doc/alsa-base/driver .txt files. In particular, see the Model option in HD-Audio.txt. Still, I haven't gotten it to work yet. Let me know if you make any progress.

Correction, I do get sound but only with the headphones.

---

### Post by rosiescape on 2010-10-20
Good to know I'm not alone. Noticed another person on here with a similar problem, see [http://ubuntuforums.org/showthread.php?t=1601053](http://ubuntuforums.org/showthread.php?t=1601053)

I'll look into your suggestion, keep me posted if you get a fix :KS

---

### Post by xzero1 on 2010-10-20
Thanks for posting the link. I have tried the ppa mentioned and its still no go, so I will be submitting a bug report to launchpad when I get a chance. If you have a different model you might want to do the same.

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/664189]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/664189")

---

### Post by rosiescape on 2010-10-21
Well I found a solution. The solution was on a German forum that I'd actually looked at a year ago when I had the same problem with 9.10 and found again.

I needed to open:
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```

and then add in this line for my model computer:

```
options snd-hda-intel model=medion-md2 power_save=10 power_save_controller=N
```

after saving and a reboot, we have sound.
Maybe with a different model listed, the solution may be of use to others. If anyone wants to check it out, the website is:

[http://forum.ubuntuusers.de/topic/medion-akoya-p4010-d-md8850-all-in-one-mini-h/#post-2233491](http://forum.ubuntuusers.de/topic/medion-akoya-p4010-d-md8850-all-in-one-mini-h/#post-2233491)

The site is in German so you may need to translate, but it should be able to give a little more information.

Thanks for the help everyone.

---

### Post by josepo on 2010-11-06
I have the exact same problem, no sound after clean installation of ubuntu 10.10... I'd like to try your workaround but.. how do i get to know my exact computer model?

---

### Post by mahjsa on 2011-01-02
Me too I had no sound using the P4010. After adding the line
```
options snd-hda-intel model=medion-md2
```
or
```
options snd-hda-intel model=targa
```

to /etc/modprobe.d/alsa-base.conf I had sound. The only drawback is that you have to set the headphone checkmark to actually hear the inbuilt speakers. Maybe a little strange at first sight, but at least there's sound.

If someone else has a better solution I am happy to hear it.

---

### Post by mahjsa on 2012-12-29
I know this thread is marked as solved, but after a clean install of 12.10 I am again experiencing problems with the sound. Even after trying the module.options that worked in 10.10 I still have only sound on the headphones.
I have been able to trace the problem to pulseaudio by trying pavucontrol. When I mute and unmute sound (PULSE sound-indicator) I hear the sound briefly only when I unmute. After that it stays silent (except when I use headphones).

---

