---
title: "No HDMI audio on Radeon HD 7770"
date: 2016-01-30
forum: Multimedia Software
---

### Post by linux-klomp on 2016-01-30
I'm running Ubuntu 14.04.3 LTS and sound has been fine for speaker and headphone usage.
But I'm now trying to record video via an HD Video Capture card in-line with my HDMI connected monitor.
Video is being recorded, but there is no sound.

According to [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) it should work out of the box.
I looked at the alsamixer, but it did not list the Radeon card.

I even tried this suggestion to no avail:
```
echo "options radeon audio=1" | sudo tee /etc/modprobe.d/radeon.conf
```
How do I get ALSA to detect my HDMI card?

```
!!Soundcards recognised by ALSA
!!-----------------------------

 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfeaf4000 irq 16
 1 [CAMERA         ]: USB-Audio - USB2.0 PC CAMERA
                      ARKMICRO USB2.0 PC CAMERA at usb-0000:00:12.2-6, high speed


!!PCI Soundcards installed in the system
!!--------------------------------------

00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA)
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series]

```
What am I missing? ](*,)

See all of my [alsa-info]("http://www.alsa-project.org/db/?f=59aaaf16db1cc0bce7bf3f7d9379b467efedaf7b") .

Thanks for your time educating me!

---

### Post by Yellow Pasque on 2016-01-30
You disabled it:
```
snd_hda_intel: enable=1,0
```

---

