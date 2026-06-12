---
title: "Odd hda-intel sound problem"
date: 2008-11-08
forum: Multimedia Software
---

### Post by nunquamsecutus on 2008-11-08
My motherboard has Realtek ALC1200 onboard audio.  It works but not automatically.  On boot I have no audio and aplay -l gives me: 
```
aplay: device_list:215: no soundcards found...
```
If I do a "sudo modprobe -r snd-hda-intel" and then "sudo modprobe snd-hda-intel" then aplay -l gives me:
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC885 Analog [ALC885 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC885 Digital [ALC885 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
and I have audio.  The audio portion of lspci -v is:
```
00:07.0 Audio device: nVidia Corporation Realtek ALC1200 8-Channel High Definition Audio Codec (rev a1)
	Subsystem: Giga-byte Technology Device a002
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at f8100000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```
Just doing a "sudo modprobe snd-hda-intel" doesn't fix the problem, I have to remove it first.  So the module is there but isn't being used?  I don't know, I'm confused.  Thanks for any help you can give me.

---

### Post by zietbukuel on 2008-11-12
I have the same card and the same problem, please HELP!!!!

---

### Post by markbuntu on 2008-11-12
This is from my guide, specific solutions for the ALC1200.

If you have an ALC 1200 sound chip (ASUS P5QL-EM mobo) you need ALSA 1.0.17 or 1.0.18rc which there is a link to below. Upgrade and add the following line to the end of the /etc/modprobe.d/alsa-base file:
Code:

options snd-hda-intel probe_mask=1

(Thanks to Nominar for hunting that down in the Fedora forums)

If you want to upgrade ALSA to 1.0.17 or 1.0.18 to get support for your sound device, a link is provided below. The script does not follow standard Ubuntu or Debian packaging so you will be unable to revert to your old installation and may have to run the script again after kernel updates to get your sound back. ALSA 1.0.17 is included in Intrepid by default so you will not have this problem if you upgrade to Intrepid. Consider yourself warned.

[http://ubuntuforums.org/showthread.php?t=962695](http://ubuntuforums.org/showthread.php?t=962695)

The guide this was taken from is here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by nunquamsecutus on 2008-11-13
I should have probably been more specific in my original post, but I'm actually running intrepid (x64).  I just checked and synaptic informs me that I have alsa-base version 1.0.17.dfsg-2ubuntu1 installed.  I'll try adding the line to my /etc/modprobe.d/alsa-base and see if that fixes things.

Update:
So I tried adding "options snd-hda-intel probe_mask=1" to the alsa-base file, and after a reboot I still have the same issue.

---

### Post by jivbot on 2008-11-26
I have exactly the same configuration and problem.

However every now and sound works when I boot. I can find no pattern to the behavior and am completely lost. Looking across all the forums this appears to be a common problem, although with different configs.

Anyone got any ideas, i have have exhausted everything I can think of and those of a great many others.

---

