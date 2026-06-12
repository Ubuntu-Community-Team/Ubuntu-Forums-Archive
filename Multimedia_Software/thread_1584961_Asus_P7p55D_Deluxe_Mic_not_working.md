---
title: "Asus P7p55D Deluxe Mic not working"
date: 2010-09-29
forum: Multimedia Software
---

### Post by guifreme on 2010-09-29
Hi guys
i have an Asus P7p55D Deluxe motherboard
and the audio seems to be working but the mic don't =/
besides that i have an Ati card that also have a hdmi output.
Someone have any ideas for what do i need to do?

---

### Post by lidex on 2010-09-30
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=6stack-digout  
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

