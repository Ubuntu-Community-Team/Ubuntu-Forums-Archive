---
title: "[SOLVED] PCI Sound loses to on-board"
date: 2008-10-27
forum: Multimedia Software
---

### Post by mfarquhar on 2008-10-27
My Motherboard has an on-board sound controller, I also have a PCI Sound card I added a few months back (wanted full-duplex). Until this problem cropped up, I had ceased using the on-board sound.

I (fresh) installed Xubuntu 8.04 a few days ago, the PCI sound worked fine. Fast forward and after needing to boot to the Windows Install, and then boot back to Xubuntu the next day, the PCI sound no longer worked (the video drivers too, but that was easier to fix).

I tried some of the steps in the [_sticky topic about sound problems_]("http://ubuntuforums.org/showthread.php?t=205449"), uninstalled and reinstalled the sound packages via the commands given
```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

sudo apt-get install linux-sound-base alsa-base alsa-utils gdm xubuntu-desktop
```(my gdm and xubuntu desktop packages were also removed so I had to add them to the command)

still no luck, I know the card is still detected (see below), and I know that it *can* work, because it did before, and the alsa site has my driver listed:
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-C-Media](http://www.alsa-project.org/main/index.php/Matrix:Vendor-C-Media)
[http://www.alsa-project.org/main/index.php/Matrix:Module-cmipci](http://www.alsa-project.org/main/index.php/Matrix:Module-cmipci)

but I'm not sure what I should try from here. It's no longer a major problem, as I discovered that the onboard works in the meantime, but I'd like to figure out why it doesn't work, especially after it used to...:confused:

aplay -l returned this
```
**** List of PLAYBACK Hardware Devices ****
card 0: CS4281 [Cirrus Logic CS4281], device 0: CS4281 [CS4281]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8738 [C-Media CMI8738], device 0: CMI8738 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8738 [C-Media CMI8738], device 1: CMI8738 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8738 [C-Media CMI8738], device 2: CMI8738 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

lspci -v returned this about the sound cards
```
00:0b.0 Multimedia audio controller: Cirrus Logic Crystal CS4281 PCI Audio (rev 01)
	Flags: bus master, medium devsel, latency 32, IRQ 9
	Memory at febf7000 (32-bit, non-prefetchable) [size=4K]
	Memory at febe0000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

00:12.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
	Subsystem: C-Media Electronics Inc CMI8738/C3DX PCI Audio Device
	Flags: bus master, medium devsel, latency 32, IRQ 10
	I/O ports at ec00 [size=256]
	Capabilities: <access denied>
```

---

### Post by HittingSmoke on 2008-10-27
Have you tried just disabling the onboard in your BOIS settings?

---

### Post by mfarquhar on 2008-10-27
> **HittingSmoke said:**
> Have you tried just disabling the onboard in your BOIS settings?
To be honest, I'm a little fearful of messing around in the BIOS disabling things...

I have tried changing the defaults and such in the programs to use the Card, but that doesn't seem to work. Are you suggesting that removing the option of the on-board in the BIOS would force everything (like something crucial I'm not seeing) to default to the Card?

---

### Post by mfarquhar on 2008-10-27
Now this just seems bizarre, I ran a system update, rebooted, and now it's back to working right :-s

Solved (I Guess)

after another round of reboots with it switching between the onboard and the card, i followed the advice of disabling the onboard, and that seems to have fixed the problem.
thnx for the help

---

