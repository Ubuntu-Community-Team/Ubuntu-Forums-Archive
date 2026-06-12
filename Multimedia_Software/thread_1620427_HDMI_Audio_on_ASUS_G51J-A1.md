---
title: "HDMI Audio on ASUS G51J-A1"
date: 2010-11-13
forum: Multimedia Software
---

### Post by WIGGMPk on 2010-11-13
HDMI Video works when connected to my Plasma TV, but absolutely no audio has been working via HDMI. Speaker and Headphone audio works fine..


```
wiggmpk@LUGGS-ASN:~$ nvidia-settings -v

nvidia-settings:  version 260.19.12  (buildd@americium)  Sat Oct 16 01:06:52 UTC 2010
  The NVIDIA X Server Settings tool.

  This program is used to configure the NVIDIA Linux graphics driver.
  For more detail, please see the nvidia-settings(1) man page.

  Copyright (C) 2004 - 2010 NVIDIA Corporation.

```

```
wiggmpk@LUGGS-ASN:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC663 Analog [ALC663 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC663 Digital [ALC663 Digital]
  Subdevices: 1/1

```

```
wiggmpk@LUGGS-ASN:~$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.23.

```

```
wiggmpk@LUGGS-ASN:~$ uname -r
2.6.35-22-generic

```

nVidia Geforce GTX 260M

Ubuntu 10.10 & Ubuntu 10.04.1 (both 64 bit)

I have searched 100's of posts and tried various 'tricks' like unmuting the channels with alsamixer. Installing the drivers from Realtek with no joy.

Any thoughts..? Need more information..?

---

### Post by WIGGMPk on 2010-11-20
Bump..

Anyone..? Anyone..?

Bueller..?

Bueller..?

---

### Post by axept on 2010-11-20
If you go to "Sound Preferences", do you find HDMI output ?

---

### Post by WIGGMPk on 2010-11-20
No mention of HDMI anywhere..

---

### Post by axept on 2010-11-20
And the drivers for your video card is installed ? In "Additional Drivers"?

---

### Post by sydbat on 2010-11-20
WIGGMPk - I am in a similar boat. NVidia GT220. Sound from motherboard (via 3.5 plug) works great. HDMI, not so much.

I have noticed that, while I can see the NVidia HDMI and "unmute" in alsamixer, and see the levels moving in the Pulse Volume control app, there is no sound coming out of any speaker.

When I run```
cat /proc/asound/card1/eld*
```I get this```
monitor_present		0
eld_valid		0
monitor_name		
connection_type		HDMI
eld_version		[0x0] reserved
edid_version		[0x0] no CEA EDID Timing Extension block present
manufacture_id		0x0
product_id		0x0
port_id			0x0
support_hdcp		0
support_ai		0
audio_sync_delay	0
speakers		[0x0]
sad_count		0

monitor_present		1
eld_valid		1
monitor_name		SHARP HDMI
connection_type		HDMI
eld_version		[0x2] CEA-861D or below
edid_version		[0x3] CEA-861-B, C or D
manufacture_id		0x104d
product_id		0x101e
port_id			0x20000
support_hdcp		0
support_ai		0
audio_sync_delay	0
speakers		[0x1] FL/FR
sad_count		1
sad0_coding_type	[0x1] LPCM
sad0_channels		2
sad0_rates		[0xe0] 44100 48000 88200
sad0_bits		[0xe0000] 16 20 24

monitor_present		0
eld_valid		0
monitor_name		
connection_type		HDMI
eld_version		[0x0] reserved
edid_version		[0x0] no CEA EDID Timing Extension block present
manufacture_id		0x0
product_id		0x0
port_id			0x0
support_hdcp		0
support_ai		0
audio_sync_delay	0
speakers		[0x0]
sad_count		0

monitor_present		0
eld_valid		0
monitor_name		
connection_type		HDMI
eld_version		[0x0] reserved
edid_version		[0x0] no CEA EDID Timing Extension block present
manufacture_id		0x0
product_id		0x0
port_id			0x0
support_hdcp		0
support_ai		0
audio_sync_delay	0
speakers		[0x0]
sad_count		0

```
I have searched and read so many threads, and tried so many things, with no positive results. I am starting to get frustrated. While I can 'live' with basic stereo sound from the on-board audio, I would really like to listen through HDMI, and watch videos with 5.1.

EDIT - Another thing I've noticed - all the info related to this says that my above eld means that the sound should be coming out of hw:1,7. However, when I play something and monitor it via the Pulse Audio volume control app, hw:1,3 unmutes SPDIF in alsamixer. (To clarify, there are 4 SPDIF's in alsamixer...SPDIF=hw:1,3, SPDIF 1=hw:1,7, etc).

Why is the sound trying to come out of a supposedly unusable output?

---

### Post by axept on 2010-11-20
> **sydbat said:**
> WIGGMPk - I am in a similar boat. NVidia GT220. Sound from motherboard (via 3.5 plug) works great. HDMI, not so much.

I have noticed that, while I can see the NVidia HDMI and "unmute" in alsamixer, and see the levels moving in the Pulse Volume control app, there is no sound coming out of any speaker.

When I run```
cat /proc/asound/card1/eld*
```I get this```
monitor_present		0
eld_valid		0
monitor_name		
connection_type		HDMI
eld_version		[0x0] reserved
edid_version		[0x0] no CEA EDID Timing Extension block present
manufacture_id		0x0
product_id		0x0
port_id			0x0
support_hdcp		0
support_ai		0
audio_sync_delay	0
speakers		[0x0]
sad_count		0

monitor_present		1
eld_valid		1
monitor_name		SHARP HDMI
connection_type		HDMI
eld_version		[0x2] CEA-861D or below
edid_version		[0x3] CEA-861-B, C or D
manufacture_id		0x104d
product_id		0x101e
port_id			0x20000
support_hdcp		0
support_ai		0
audio_sync_delay	0
speakers		[0x1] FL/FR
sad_count		1
sad0_coding_type	[0x1] LPCM
sad0_channels		2
sad0_rates		[0xe0] 44100 48000 88200
sad0_bits		[0xe0000] 16 20 24

monitor_present		0
eld_valid		0
monitor_name		
connection_type		HDMI
eld_version		[0x0] reserved
edid_version		[0x0] no CEA EDID Timing Extension block present
manufacture_id		0x0
product_id		0x0
port_id			0x0
support_hdcp		0
support_ai		0
audio_sync_delay	0
speakers		[0x0]
sad_count		0

monitor_present		0
eld_valid		0
monitor_name		
connection_type		HDMI
eld_version		[0x0] reserved
edid_version		[0x0] no CEA EDID Timing Extension block present
manufacture_id		0x0
product_id		0x0
port_id			0x0
support_hdcp		0
support_ai		0
audio_sync_delay	0
speakers		[0x0]
sad_count		0

```
I have searched and read so many threads, and tried so many things, with no positive results. I am starting to get frustrated. While I can 'live' with basic stereo sound from the on-board audio, I would really like to listen through HDMI, and watch videos with 5.1.

EDIT - Another thing I've noticed - all the info related to this says that my above eld means that the sound should be coming out of hw:1,7. However, when I play something and monitor it via the Pulse Audio volume control app, hw:1,3 unmutes SPDIF in alsamixer. (To clarify, there are 4 SPDIF's in alsamixer...SPDIF=hw:1,3, SPDIF 1=hw:1,7, etc).

Why is the sound trying to come out of a supposedly unusable output?

When you playing a song/video, go to terminal and run alsamixer.
Go to the right to you find S/PDIF, try to mute/unmute them. Maybe one must be muted and the others not, just try different ways. If/when you get sound, then run sudo alsactl store in terminal..

Worked for my Nvidia HDMI sound problem.

---

### Post by sydbat on 2010-11-20
> **axept said:**
> When you playing a song/video, go to terminal and run alsamixer.
Go to the right to you find S/PDIF, try to mute/unmute them. Maybe one must be muted and the others not, just try different ways. If/when you get sound, then run sudo alsactl store in terminal..

Worked for my Nidia HDMI sound problem.Tried all combos, no sound. Trying yet another set of instructions. I'll let you know if they work!

---

### Post by WIGGMPk on 2010-11-20
@axept & @sydbat

I tried running a youtube video while HDMI video was connected to my TV and playing around with the SPDIF muting in alsamixer with no success..

aplay -l

Still doesnt show any HDMI devices..


@axept

The drivers are installed from Jockey, yes..

I use a more 'bleeding edge' version from a PPA, but I have tried all drivers..

---

### Post by sydbat on 2010-11-20
OK. Some sound. 5.1 too!!

However, it is just through aplay -D hw:0,7 /path/to/file.wav. No other sound yet.

How I got to this point - I followed the instructions on the [xbmc]("http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240") page, specifically the stuff about > set options in /etc/modprobe.d/sound.conf depending on your card.then> options snd-hda-intel enable_msi=0 index=1
This made my NVidia HDMI the default card.

I also changed the 'internal' sound via PulseAudio Volume Control (under the "Configuration" tab) from "Stereo Duplex" to "Stereo Input", then I unplugged the 3.5 stereo plug from my TV. I think these were overriding the HDMI sound input to the TV.

EDIT - I went over things on the [xbmc]("http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240") page and realized I missed as step. DOH!

Here is the rest of what needs to be done.> PulseAudio Configuration

If using PulseAudio, add the following line to /etc/pulse/default.pa:

load-module module-alsa-sink device=hw:1,3

Where 1,3 is card#,device# for the nVidia HDMI output given by aplay -l.The line in question is commented out with a #. I removed the # and added my device info (device=hw:07). Rebooted and full 5.1 sound from HDMI. YAY!!!

---

### Post by axept on 2010-11-21
> **WIGGMPk said:**
> @axept & @sydbat

I tried running a youtube video while HDMI video was connected to my TV and playing around with the SPDIF muting in alsamixer with no success..



It sounds like your problem is something else since you dont find HDMI Output in the preferences.

---

### Post by efflandt on 2010-11-21
WIGGMPk, since **aplay -l** does not list any NVidia HDMI devices you may need a newer subversion of alsa from the ppa.  I had to do that for my GT 430 which is so new that **lspci** does not even show its model yet:

01:00.0 VGA compatible controller: nVidia Corporation Device 0de1 (rev a1)
01:00.1 Audio device: nVidia Corporation Device 0bea (rev a1)

This explains how to do that:
[https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

I ended up with 4 NVidia HDMI devices, but only one of them worked.  In **alsamixer** make sure that all the devices in **HDA NVidia** are unmuted, press **m** for any that show MM instead of 00.  Then play around with aplay until you find one that works.  For me it was:

```
aplay -D plughw:1,9 /usr/share/sounds/alsa/Front_Center.wav
```Then add the following to /etc/pulse/default.pa for the one that works:

```
load-module module-alsa-sink device=hw:1,9
```If you want the most recent nvidia (currently 260.19.21, instead of .12) go to System > Adminstration > Additional Drivers, **remove** nvidia, reboot:

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates

sudo apt-get update
```Then go back to Additional drivers and **activate** nvidia, reboot.

---

### Post by sydbat on 2010-11-21
An update.

I only seem to be getting full 5.1 surround when running aplay -D hw:0,7 /path/to/file.wav. I do get basic stereo from everything else (so far), but when I put a DVD in and run it with Totem, VLC, etc, etc, I do not get 5.1 surround at all. Changing sound settings in these media players has no effect.

Why does only aplay (via terminal) give me 5.1 surround? Is there a way to run all my sound through aplay, without use of the terminal?

WIGGMPk - have you tried the solutions efflandt suggests? How about the ones that got my sound working? If so, do you have sound now??

---

### Post by sydbat on 2010-11-26
Another update - 5.1 on almost everything except when I play a DVD with a media player. Files with AC3 or other 5.1 sound on my HDD play perfectly, as do YouTube videos and other online video/audio surround sources.

Also, I notice that there is a second or two delay in sound, when I play a new bit of audio. When there is no audio playing, my home theatre system does not register the input. Is there a way of making the HDMI audio connection persistent? I have Googled alot, but have not found a solution yet.

---

### Post by oldspammer on 2011-05-03
After trying quite a few things, I got my HDMI sound to work but with static involved in the output sound.  It would play sounds from applications and all, but with this extra noise. :(

After rebooting, though, the system had no sound again. :confused: :(

Now, a few weeks later, and I've applied some of the latest updates--Wow, after rebooting, the HDMI sound came on by itself just like it had done a long time ago after the initial installation!  :) No static that I can notice.  :) Hopefully, my problems with this are over until the next time a developer decides to tweak the code again and ruin things for all of us Nvidia HDMI users?

I was hoping to use the Nvidia drivers to use the CUDA GPU's to do transcoding recompression of a bunch of my recorded videos...  Too bad that the ubuntu system menu item for screen display size is unfriendly with the latest Nvidia drivers / vice versa?

I've got a Zotac Nvidia GTX 570 w/ 260.19.36 driver 64-bit running on a Sharp 52 inch HDTV at 1080p.

When the Nvidia control panel for the display is run, it cannot save the display settings into the x config file to make the setting come up after rebooting.  I now have to run Nvidia control panel to set the resolution / settings, then run the ubuntu control to save the settings to the x config file.  But this is not too bad a problem.
=================
Update: 

Upon rebooting with the Sharp 52 inch HDTV initially powered off, the settings permanently undid themselves, and now I have no sound again.

Cold booting the computer  with the TV already powered on made no effect on the malfunctioning sound settings.  The Sound Preferences applet NEVER is able to undo the trouble even though the choices available match my hardware exactly.  Upon rebooting and cold booting after Sound Preferences are tweaked to be the "correct ones" selecting Nvidia HDMI, the system remains without any HDMI audio.

Some kind of system level boot-up software seems to have its own preference as to the system settings so that when the HDMI TV was not there at boot up this one time, the prior working / good settings were erased and replaced with bogus ones "thought "by the system programmers to be "adequate replacements"--irreparably damaging the entire HDMI audio capability for subsequent boot ups.

---

