---
title: "No sound from internal speaker - MSI M6275"
date: 2010-06-14
forum: Multimedia Software
---

### Post by leobin1989 on 2010-06-14
I'm just a  newbie 
After I install ubuntu, everything goes alright except sound.
I have sound when I plug in the head-phone(sound for headphone)
But I cannot find how to play sound for internal speakers( 1 subwoofer + 2 speakers)
This is my device's information 

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio  Controller (rev 03)
    Subsystem: Micro-Star International Co., Ltd. Device 6740
    Flags: bus master, fast devsel, latency 0, IRQ 30
    Memory at fdef8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

---

### Post by ShiroKitsune on 2010-07-28
Bump!

I have been looking for a fix for some time now for the same laptop, if you have got your working could you please post the fix for it, thank ;)

---

### Post by lidex on 2010-07-30
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel probe_mask=1 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.

---

### Post by abeam on 2011-01-10
I've got the same computer and almost the same problem. Unlike the OP, I don't have sound period, including headphones. I've been messing around with drivers for days, and I think all I've done is clutter up the drive. I don't even know if the drivers are the problem.

So in addition to no sound, when I go to the Hardware tab in Sound Preferences, it's blank; no soundcards to choose from. Also, when I type alsamixer into the terminal, it says, "cannot open mixer: No such file or directory."

I'm also a total Linux beginner. All I have is a rudimentary understanding of how to work a prompt screen (from jury rigging early 90s games to work), and the will to use it.

---

### Post by lidex on 2011-01-11
First re-install alsa. Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```

---

### Post by abeam on 2011-01-11
> **lidex said:**
> First re-install alsa. Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```

I entered that and got, "sudo: aptitude: command not found." In other commands that began with aptitude, replacing "aptitude" with "apt-get" did the trick (I don't know if it applies to here), but when I did that, I got, "E: Invalid operation reinstall."

I'm thinking about a clean reinstall of Ubuntu and going from there. Good idea? There are several programs, alsamixer being one of them, that worked when I first installed Ubuntu last week, but for whatever reason, they don't anymore.

EDIT: I suppose it's worthwhile to mention that I'm using 10.10, unlike the OP.

---

### Post by lidex on 2011-01-13
That syntax probably only works correctly with aptitude. It's no longer installed by default but is good to have.
```
sudo apt-get install aptitude
```

---

### Post by abeam on 2011-01-13
Alright that worked, and alsamixer is functional again.

EDIT: alsa works, but there's still no sound.

---

