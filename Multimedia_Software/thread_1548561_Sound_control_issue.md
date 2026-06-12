---
title: "Sound control issue"
date: 2010-08-08
forum: Multimedia Software
---

### Post by KEric on 2010-08-08
Hello,

Yesterday I was having an issue with my sound, it just suddenly stopped working, and it said "dummy output" on my sound options. So after tinkering around I decided to upgrade from 9.10 to 10.04, which did not solve the problem.

I eventually stumbled on a blog which told me to upgrade from ALSA 1.0.21 to ALSA 1.0.23. Doing this got my sound restored, but my issue is that when I change the volume on my indicator applet it does not affect the actual volume at all, any other volume controller like Pulseaudio volume controller does not change it either, the only thing that changes it, is the Gnome ALSA Mixer.

Anyone know what it could be?

Here's what I have for my sound chipset

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC665 Analog [ALC665 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by KEric on 2010-08-08
Is there any additional information I could post to help diagnose the issue?

---

### Post by simosx on 2010-08-08
> **KEric said:**
> Is there any additional information I could post to help diagnose the issue?

Obtain the full soundcard details with
[FONT="Courier New"]wget [www.alsa-project.org/alsa-info.sh](www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh
[/FONT]When prompted, say Yes to send the data to alsa-project.org (Alsa website) and post here the URL you will be given. In this way we can see what hardware you have and if there are any problems.

---

### Post by KEric on 2010-08-08
Thank you Simosx, I've run the sound card details, here's the link to my details.

[http://www.alsa-project.org/db/?f=894d89d493383485de5323a37b2cb9911076aa78](http://www.alsa-project.org/db/?f=894d89d493383485de5323a37b2cb9911076aa78)

It's bizarre, my sound works, it's just the only way I can change the volume is with the alsa mixer, the indicator applet is visible, and I can change the volume on it, or mute it, but it doesn't affect the actual sound at all. It seems like it could be a software thing, but I'm not sure.

---

### Post by Yellow Pasque on 2010-08-09
The volume applet is for pulseaudio, so maybe some apps are playing sound directly to the ALSA device. This happens with the upgrade script. To remedy: [http://ubuntuforums.org/showthread.php?t=1455816](http://ubuntuforums.org/showthread.php?t=1455816)

---

### Post by KEric on 2010-08-09
Hi, Temujin, 

I added those lines into asound.conf, when I opened the file it was blank, but I inserted it anyways. After doing that and rebooting my sound doesn't work in any application. 

I also tried Vectorferret's fix too, but that did not work either.

---

### Post by simosx on 2010-08-09
Your alsa-info output shows the following lines at the end

[I][   15.794804] hda_codec: ALC665: SKU not ready 0x598301f0
[   15.795039] hda_codec: ALC665: BIOS auto-probing.
[/I]

This might be indication to set manually the 'model' of the sound card, so that the mixer works. See more at [http://www.alsa-project.org/main/index.php/Help_To_Debug_Intel_HDA](http://www.alsa-project.org/main/index.php/Help_To_Debug_Intel_HDA)

In addition, you have two sound cards, an Intel and an NVidia. Your problem could be that some apps may look at the other card; for example, using the mixer of the wrong card.

---

### Post by KEric on 2010-08-09
Hey guys, 

I was doing some fiddling around in alsamixer like your trouble shooting guide says, and this may helps us with the problem. It appeared after Temujin's suggestion, so it seems like his worked for the applet atleast.

So, basically now on alsamixer there's 3 soundcards, default, Intel and Nvidia. "Default" sound card is titled "Pulseaudio" which changes with my sound applet. My real soundcard is "Intel" and I can select it in Alsamixer too, and change the volume and such, but Pulseaudio seems to "overpower" it. NVidia, isn't really anything at all. So, the problem seems like it could be a model parameter thing in the configuration. How do I access that to change the model?

Also, would screenshots of the soundcard selection of alsamixer help? Or is my explanation okay?

---

### Post by lidex on 2010-08-09
To change the model:
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=auto 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

Try that one for now. What do you get for this:
```
sudo dmidecode -t baseboard
```

---

