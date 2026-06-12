---
title: "Sound problem with Asus SupremeFX X-Fi"
date: 2010-05-31
forum: Multimedia Software
---

### Post by SavageHcky7 on 2010-05-31
I cannot get anything other than "Analog Stereo" to work with Lucid and an Asus SupremeFX X-Fi card.  I should be able to get Surround 5.1, just like I am able to when I boot the same hardware with Windows, right?

Any help would be appreciated!

Here is some system info:

From aplay -l:
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

From lspci -v:
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
	Subsystem: ASUSTeK Computer Inc. Device 8334
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f9ff8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

---

### Post by lidex on 2010-06-01
Can you post the output of these terminal commands for me please:
```
uname -a
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by lidex on 2010-06-01
What do you have set as your profile in sound preferences on the hardware tab?

---

### Post by SavageHcky7 on 2010-06-01
Hello!

Thank you for your reply.  Here is the extra information:

PC is a desktop with an Asus Maximus Formula II motherboard.

$uname -a
Linux  2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux

$cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.

$ head -n 1 /proc/asound/card*/codec#*
Codec: Analog Devices AD1989B

I have "Analog Stereo Output" selected as my profile, as that is the only one (besides "Analog Stereo Duplex") that results in sound.  I have tried "Analog Surround 5.1" but I get terrible sound, and from only 1 or 2 speakers.

Thanks again for your help!

---

### Post by lidex on 2010-06-02
3 or 6 audio jacks? spdif yes or no?

---

### Post by SavageHcky7 on 2010-06-02
3 connections to a Logitech Z-640 speaker system (soundcard does have 6 possible connections - line in, line out/front speaker out, mic in, center/sub out, rear speaker out, side speaker out) in addition to the SPDIF).  No SPDIF connection.  I have connections to line out/front speaker out, center/sub out, and rear speaker out.

For what it is worth, this setup sounds good when I boot into Windows - all speakers are functioning properly.

---

### Post by lidex on 2010-06-02
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=6stack-dig 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

---

### Post by SavageHcky7 on 2010-06-05
Thank you!!  That seemed to help!  I noticed that the 'settings' under "Sound Preferences->Output" (where you set Balance, Fade, etc.) acts very, very odd.  The balance slider and the fader slider have some odd link between the two of them, which makes it difficult to try to isolate the individual speakers.  I also noticed that moving the sliders there had some odd effects in the alsamixer settings.  I ended up simply using alsamixer only and that seems to be working!

Thanks again for your help!  I really appreciate it!!

---

### Post by lidex on 2010-06-05
You might also try gnome-alsamixer and pulseaudio-volume-control (pavucontrol).
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

pavucontrol
```
sudo apt-get install pavucontrol
```

---

