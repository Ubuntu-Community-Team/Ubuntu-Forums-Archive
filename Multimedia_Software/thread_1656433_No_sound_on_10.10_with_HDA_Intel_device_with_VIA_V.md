---
title: "No sound on 10.10 with HDA Intel device with VIA VT1708S codec"
date: 2010-12-30
forum: Multimedia Software
---

### Post by MikeBenza on 2010-12-30
I just built a new machine with an Asus P7P55D-E LX motherboard with onboard sound.  I can't get any sound to work.

I ran the Alsa information script (results [here]("http://www.alsa-project.org/db/?f=822c267b825fb3997ec74f0e3b0c39fb955760cb")).  It seems the VIA VT1708S codec isn't in Alsa 1.0.23.  However, ALSA [claims support was added in 1.0.18rc3]("http://www.alsa-project.org/main/index.php/Changes_v1.0.18rc2_v1.0.18rc3") (search for VT1708S).

How can I get sound?

---

### Post by kostkon on 2010-12-30
What is the output of
```
aplay -l
```

Did you try to setup your sound in System -> Preferences -> Sound?

---

### Post by MikeBenza on 2010-12-30
```
mike@MikesDesktop:/tmp$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: Intel [HDA Intel], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Yes, I tried to set it up in Sound Preferences.  I've tried every combination of hardware, profiles, and devices.  Nothing works.

---

### Post by kostkon on 2010-12-30
Try installing gnome-alsamixer and check your hardware volume levels and switches.

Then try again all the available configuration options in your sound prefs.

---

### Post by Yellow Pasque on 2010-12-30
You can try the ALSA upgrade script with -s to pull the development snapshot. Judgindg from the documentation, some support has been added for VIA codecs since the 1.0.23 release
> VIA VT17xx/VT18xx/VT20xx
========================
  auto		BIOS setup (default)

Oops, here's the linky link: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

---

### Post by MikeBenza on 2010-12-31
> **kostkon said:**
> Try installing gnome-alsamixer and check your hardware volume levels and switches.

Then try again all the available configuration options in your sound prefs.

That worked, but I had to unmute the channels every time and fiddle with the hardware/devices selected every time I rebooted.

> **Temüjin said:**
> You can try the ALSA upgrade script with -s to  pull the development snapshot. Judgindg from the documentation, some  support has been added for VIA codecs since the 1.0.23 release


Oops, here's the linky link: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

That completely got rid of sound.  After I finished, asound wasn't running.  The restore option didn't work either, so now I'm worse off :(.  (Don't beat yourself up...this is a next-to-brand-new install, so it'll be easy to replace)

The log from the failed restore is attached.  I don't have the log from the broken installation because it was logged in /tmp/ and I blindly followed the instructions to reboot ;)

---

### Post by MikeBenza on 2011-01-01
So, I reinstalled Ubuntu and I bought a new sound card.  It's got a Creative Labs CA0106 chipset in it....which ALSA [says has unknown support](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs), but ALSA also [says is supported](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs).  Whenever I try to play a sound I just get static.

Interestingly, when I installed the sound card, the onboard sound hardware  and the sound hardware on the graphics card stopped appearing in gnome-volume-control.

Can anyone help here?

---

### Post by MikeBenza on 2011-01-01
I uninstalled the new card and I was able to get the onboard sound working.  And this time it remembers my muting/unmuting.

---

