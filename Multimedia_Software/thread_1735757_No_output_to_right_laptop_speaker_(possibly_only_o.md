---
title: "No output to right laptop speaker (possibly only one speaker)"
date: 2011-04-21
forum: Multimedia Software
---

### Post by kiddykoff on 2011-04-21
Hello forum,

I just got a new Acer Aspire 5552-7803 laptop. It came with windows 7 and from there i was able to hear right and left output using the system utilities. It doesn't sound like the two channels are separated and may be coming from the same speaker.

I now installed Ubuntu 10.10 64 bit and copied over my home folder from my previous laptop.

The problem is that my sound wasn't that great and I found out my right speaker isn't working. I think the laptop may have only one speaker. Does anyone have the same issue?

i ran lspci | grep -i audio and got:
```
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]

```
aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC272X Analog [ALC272X Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I tried removing and reinstalling linux-sound-base, alsa-base, and alsa utils and rebooting. It didn't work.

and of course i tried out Alsamixer. Everything seemed okay there.

Edit: I forgot to mention, plugging in my headphones allows me to hear the right channel.

---

### Post by kiddykoff on 2011-04-22
bump

---

### Post by seaghan on 2011-05-02
bump again

Hey, I have the same problem, left channel only speaker.

Im using Fedora 15 and my smolt profile shows that the analogue audio device is a
[ATI Technologies Inc SB600 Azalia]("http://www.smolts.org/reports/view_device/SBx00%20Azalia%20%28Intel%20HDA%29")
which is a varient of the Intel HDA?

further googling showed that there is an issue with certain models of this and it requires that hda-verb be installed and certain 'verbs' set on the devices profile. 

I have no idea of the precise settings for this particular model, as my google searching only brought up models released many years ago and/or using older kernel versions.

Have you had any luck in getting both channels working?

Apparently, in the past, the problem has been fixed before with kernel updates, so it could be just a problem that will fix itself over time.

When i do a ```
 dmesg | grep hda 
``` i get an error saying there was no SSID found for the device, therefore no pin config so it would appear it defaulted to another device profile, which is obviously the wrong one.
```

[sean@acer-as5552 ~]$ dmesg | grep hda
[   31.539284] ALSA sound/pci/hda/patch_realtek.c:1528: SKU: Nid=0x1d sku_cfg=0x4016892d
[   31.539289] ALSA sound/pci/hda/patch_realtek.c:1530: SKU: port_connectivity=0x1
[   31.539293] ALSA sound/pci/hda/patch_realtek.c:1531: SKU: enable_pcbeep=0x1
[   31.539296] ALSA sound/pci/hda/patch_realtek.c:1532: SKU: check_sum=0x00000006
[   31.539298] ALSA sound/pci/hda/patch_realtek.c:1533: SKU: customization=0x00000089
[   31.539301] ALSA sound/pci/hda/patch_realtek.c:1534: SKU: external_amp=0x5
[   31.539304] ALSA sound/pci/hda/patch_realtek.c:1535: SKU: platform_type=0x1
[   31.539306] ALSA sound/pci/hda/patch_realtek.c:1536: SKU: swap=0x0
[   31.539309] ALSA sound/pci/hda/patch_realtek.c:1537: SKU: override=0x1
[   31.539484] hda_codec: ALC272X: BIOS auto-probing.
[   31.539490] ALSA sound/pci/hda/hda_codec.c:4633: autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0)
[   31.539494] ALSA sound/pci/hda/hda_codec.c:4637:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   31.539497] ALSA sound/pci/hda/hda_codec.c:4641:    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[   31.539500] ALSA sound/pci/hda/hda_codec.c:4642:    mono: mono_out=0x0
[   31.539503] ALSA sound/pci/hda/hda_codec.c:4646:    inputs:
[   31.539505] ALSA sound/pci/hda/hda_codec.c:4652: 
[   31.540544] ALSA sound/pci/hda/patch_realtek.c:1585: realtek: No valid SSID, checking pincfg 0x4016892d for NID 0x1d
[   31.540547] ALSA sound/pci/hda/patch_realtek.c:1601: realtek: Enabling init ASM_ID=0x892d CODEC_ID=10ec0272
[   60.082115] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.

```

---

### Post by kiddykoff on 2011-05-04
i haven't come across any new information, but i've been busy with school. I came across this post just now, but it doesn't offer any new information.
[http://ubuntuforums.org/showthread.php?t=496072](http://ubuntuforums.org/showthread.php?t=496072)

---

### Post by lidex on 2011-05-05
Try updating your alsa-driver-modules.
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

---

### Post by kiddykoff on 2011-05-22
that didn't do anything for me lidex.

---

### Post by lidex on 2011-05-22
Let's see your alsa-info.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications-> Accessories-> Terminal"]

---

### Post by perfesir on 2011-06-10
Check your hardware specs.  The Acer AS5552-7803 has only one speaker.  Most sellers do not mention it, but Fry's lists it that way.

---

### Post by kiddykoff on 2011-06-15
here is the output,

[http://www.alsa-project.org/db/?f=1aa904a29531002e2ac043656d776e0c090429af](http://www.alsa-project.org/db/?f=1aa904a29531002e2ac043656d776e0c090429af)

---

### Post by lidex on 2011-06-15
I think perfesir had it right - mono speaker setup:
```
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 63 [98%] [-1.00dB] [on]
```
Some of the reviews specifically mentioned poor sound quality. You could plug powered speakers into the line/headphone out.

---

### Post by halibaitor on 2011-06-15
Acer is kinda "famous" for doing this.  They will build an otherwise great computer, then put a mono audio system in it. :(

Check out the audio portion of this spec sheet.
[http://support.acer.com/acerpanam/notebook/2010/Acer/Aspire/Aspire5552/Aspire5552sp2.shtml]("http://support.acer.com/acerpanam/notebook/2010/Acer/Aspire/Aspire5552/Aspire5552sp2.shtml")

---

