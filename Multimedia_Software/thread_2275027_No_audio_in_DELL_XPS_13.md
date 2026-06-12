---
title: "No audio in DELL XPS 13"
date: 2015-04-23
forum: Multimedia Software
---

### Post by bach on 2015-04-23
Today I installed Ubuntu 15.04 (desktop edition, 64 bit) on a DELL XPS 13 (model 9343) notebook. Prior to installation, I upgraded the computer bios to A03. The kernel I am running is 3.19.0-15. I have no audio/sound. Here is some info: 

cribari@darwin4:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Suggestions are welcome. Thank you.

---

### Post by bach on 2015-04-23
More info... 

cribari@darwin4:~$ lspci -nn | grep -i audio
00:03.0 Audio device [0403]: Intel Corporation Broadwell-U Audio Controller [8086:160c] (rev 09)
00:1b.0 Audio device [0403]: Intel Corporation Wildcat Point-LP High DefinitionAudio Controller [8086:9ca0] (rev 03)
cribari@darwin4:~$

---

### Post by Yellow Pasque on 2015-04-24
More info please: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)
Are you trying to use the HDMI audio or not?

---

### Post by bach on 2015-04-24
I found the solution in [http://bartongeorge.net/2015/04/09/4th-gen-dell-xps-13-developer-edition-available/](http://bartongeorge.net/2015/04/09/4th-gen-dell-xps-13-developer-edition-available/) . The solution: "If dual booting with Windows 8.1 and kernel 4.0 or earlier you will need to cold boot twice into the OS for audio to work."

---

### Post by lunya on 2015-04-26
I just wanted to add that I had the same problem (xps13 9343, dual boot Ubuntu 15.04 / win8.1, bios A03, kernel 3.19.0-15, no sound in either speakers or headphones), and booting twice didn't seem to fix it. In the end it turned out that in Sound Settings, Sound Effects tab, "Alert Volume" was muted (this is not something I did, it must have been set like that from the start). Once I increased the alert volume, everything went to normal.

---

### Post by cnbiz850 on 2015-06-06
Hi everyone with the new XPS 13,

I am looking to buy the laptop and looking to install Ubuntu.  Would you guys kindly share about the experience?  Does Ubuntu 15.04 run well on it?  What problems have you encountered during the installation?

---

### Post by amoun on 2015-07-25
There's a Developer's edition that comes pre-installed with Ubuntu, is here a reason not to buy that? Is it that a dual boot is wanted.
[http://www.dell.com/uk/business/p/xps-13-linux/pd](http://www.dell.com/uk/business/p/xps-13-linux/pd)

---

### Post by Patrick_Hill on 2016-04-02
I'm having some sound issues with the 9343, Win 10 and Ubuntu 16.04.  I read about the cold booting twice but that's not helping.  Here is what is happening.  At first in windows I had the red X through the sound and there were no devices, I install the realtek driver.  Once I reboot the sound is working and the realtek device is listed in my sound devices but the default device is set to the Intel sound, not the realtek sound device.  If I select the realtek device, everything works for the time being.  If I shutdown and boot into ubuntu and then back into windows the realtek device is still selected as the default when it first boots then switches to the intel one as the default by itself (I watched it, the realtek was default then it switched to the intel one in front of my eyes). If I shutdown windows, then restart into windows again(no matter how many times) the realtek device is gone completely from the list of devices and the intel one is selected again.  I have to boot back into ubuntu, then back into windows for the realtek device to show up again and then reset it as the default.  It's very annoying

---

### Post by apollo-vampirex on 2016-04-02
i have the same problem.
anybody?? HELP

---

### Post by Yellow Pasque on 2016-04-02
Do you have a Dell XPS?

---

### Post by bach on 2016-06-13
I have a Dell XPS 13 notebook (model 9343, bios A07). I had audio problems with Ubuntu and Fedora. I am now running Arch Linux and the problems persist. My model is the one with Intel i7, 3200 x 1800 resolution, touchscreen and Broadcom wireless. I run Gnome 3.20 + GDM. My problem is that I have (I2S) audio for a while and then audio crashes. I filed the following Arch bug: [https://bugs.archlinux.org/task/49556](https://bugs.archlinux.org/task/49556) . There is a discussion of the problem here: [https://bugs.archlinux.org/task/48936](https://bugs.archlinux.org/task/48936) . I do realize that Arch is Arch, Fedora is Fedora and Ubuntu is Ubuntu. Nonetheless, I believe some Dell XPS 13 9343 audio problems are common to many distros. The solution I found was to compile my own kernels using CONFIG_ACPI_REV_OVERRIDE_POSSIBLE=y .

---

