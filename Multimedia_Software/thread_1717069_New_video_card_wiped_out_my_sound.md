---
title: "New video card wiped out my sound"
date: 2011-03-29
forum: Multimedia Software
---

### Post by ratcheer on 2011-03-29
I recently installed a new evga nVidia GT 430 video card in my Ubuntu 10.10 32-bit system. This had the unforseen side effect of eliminating my sound.

I had no idea that the new video card would include a new sound module. My intent is for my system to use my Soundblaster Audigy2 soundcard in 5.1 output mode. The system still seems to be configured to do that, but the nVidia HDMI Stereo output module seems to have taken over in Sound Preferences.

Here is the output of lspci:

```
lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Device 0de1 (rev a1)
[B]01:00.1 Audio device: nVidia Corporation Device 0bea (rev a1)
02:09.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)[/B]
02:09.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
02:09.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
02:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
02:0b.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)

```

Here is the output of aplay -l:

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Audigy2 [SB Audigy 2 ZS [SB0350]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 2: Audigy2 [SB Audigy 2 ZS [SB0350]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 2: Audigy2 [SB Audigy 2 ZS [SB0350]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Audigy2 [SB Audigy 2 ZS [SB0350]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

The nVidia module has apparently "pushed" the Creative card out of the way. How do I fix this?

Tim

---

### Post by ratcheer on 2011-03-29
Ok, I got this far. I ran "cat /proc/asound/modules" and used the output to edit /etc/modprobe.d/alsa-base.conf, adding lines:

```
options snd_hda_intel index=1
options snd_intel8x0 index=2

```

Now, the system is detecting the Audigy card, first. When I rebooted, the Ubuntu startup sound played, so I know I am making some progress.

However, I still cannot get sound from audio cd's nor from flash on the web (e.g., Youtube videos).

What next?

Tim

---

### Post by Yellow Pasque on 2011-03-29
Try padevchooser package.

---

### Post by ratcheer on 2011-03-29
> **Temüjin said:**
> Try padevchooser package.

Thanks. But, I started installing it, and the package manager wanted to remove 23 other packages. That doesn't look right, to me.

Tim

---

### Post by ratcheer on 2011-03-30
Ok, I managed to get padevchooser installed without too much damage. It shows me that PA is getting the signal when I play a CD, as I can see the PA volume meter display fluctuating with the music.

I have chosen the Audigy card as the output device. But I still cannot get actual sound output, even with the speaker test applet.

I probably have things so messed up now that I will never get them back to right.

Tim

---

### Post by ratcheer on 2011-03-31
I double checked my speaker connections. They are (and have been) correct.

Tim

---

### Post by lidex on 2011-04-01
Audigy's seem to have a problem with the in/out-digital/analog switching. Try playing around in gnome-alsamixer. To quote markbuntu:> Audigy
If your Creative Audigy card is not giving you any sound, make sure the analog/digital check box in your sound mixer is unchecked. Updates seem to reset this switch regularly so keep this in mind.

---

### Post by ratcheer on 2011-04-01
Thanks for your suggestion, lidex. I found a control named "Audigy Analog/Digital Output Jack" in alsamixer and turned it Off, but still no sound.

I do still get an Ubuntu startup sound when I reboot the PC, but after it is up and I am logged in, I cannot even get a sound from "aplay /usr/share/sounds/alsa/Front_Center.wav".

Tim

---

### Post by Yellow Pasque on 2011-04-01
If you only want to use your SB card, then disable your onboard audio in the BIOS and blacklist snd-hda-intel module so HDMI audio doesn't get initialized.

---

### Post by ratcheer on 2011-04-01
Ok, I found an article that contained a suggestion that fixed the problem. I had to effectively delete, by renaming ~/.pulse directory. When I logged back on to that account, the directory was recreated and now my sound is working perfectly, again.

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

See under heading "Can someone else play a known-good sound?"

Thanks to everyone who tried to help.

Tim

---

### Post by Yellow Pasque on 2011-04-01
That was my next suggestion :/
Glad you found it on your own, though.
Oh, and I would still disable the other audios just to make sure they don't interfere.

---

### Post by ratcheer on 2011-04-01
Thanks.

Also, I tried the same thing in Natty, but it did not work there. ???

Tim

---

### Post by Yellow Pasque on 2011-04-01
Instead of renaming, it is better to delete the user-specific pulse info if it gets corrupted:
```
rm -rf .pulse*
```
Alternatively, you can create another user and see if sound works for that account. If not, the problem lies deeper..

---

### Post by ratcheer on 2011-04-01
> **Temüjin said:**
> Instead of renaming, it is better to delete the user-specific pulse info if it gets corrupted:
```
rm -rf .pulse*
```Alternatively, you can create another user and see if sound works for that account. If not, the problem lies deeper..

Thanks. I will try both suggestions in Natty.

Tim

---

### Post by lidex on 2011-04-01
> **ratcheer said:**
> Thanks. I will try both suggestions in Natty.

Tim

What's your aplay -l in natty?

---

### Post by ratcheer on 2011-04-02
Ok, I have SOLVED the problem for Natty, too, but I am a bit confused as to why it didn't get fixed, yesterday.

Today, I fixed it by creating a new user, granting Admin rights to that user, logging out, logging in as the new user, and removing the ~/.pulse directory of my main user.

However, yesterday, I booted to a recovery console and logged in as root and renamed the ~/.pulse directory of my main user. That did not fix the problem and I cannot understand why not. Maybe, as Temujin suggested above, it was because I renamed it instead of removing it, but renaming solved the problem in Maverick.

?????

Anyway, the problem is solved for all my Ubuntu installations.

Tim

---

