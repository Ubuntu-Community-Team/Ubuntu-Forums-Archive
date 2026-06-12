---
title: "Installed wrong drivers, now sound is not playing"
date: 2011-12-29
forum: Multimedia Software
---

### Post by el canadiano on 2011-12-29
Hey guys,

I've noticed that my sound quality is really horrendous in Ubuntu (in comparison to the Windows 7 installation, which isn't as bad), so I wanted to try to fix it by installing better drivers.

Clearly, I screwed up, and now I'm playing. Sound went from poor-quality to quiet, and I realize it is my fault. I'm not too sure what to do at this point.

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

According to the troubleshooting page listed above, I tried steps 1-4 and 6. Step 4 returns this.

```
awpoon@ilose-Ubuntu:~$ sudo aplay -l
aplay: device_list:240: no soundcards found...
```

Step 6 returns this.

```
awpoon@ilose-Ubuntu:~$ lspci -v | grep -A7 -i "audio"
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
	Subsystem: ASUSTeK Computer Inc. Device 1ae3
	Flags: bus master, fast devsel, latency 0, IRQ 5
	Memory at df600000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5) (prog-if 00 [Normal decode])
awpoon@ilose-Ubuntu:~$ sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
sudo: aptitude: command not found
```

For some reason, I thought I was installing something from Realtek... The English in the manuals are horrible.

EDIT: [https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

I got the sound working again using the command line Alsa ppa. I think I'll just stick with this. Sound quality is fine when it's on headphones.

---

### Post by lidex on 2011-12-31
Know your mixers. Sometimes simply tweaking levels makes a massive difference. Louder is not always better.
**Alsamixer**
Using a Terminal="Applications->Accessories->Terminal"
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

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

---

