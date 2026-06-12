---
title: "Audio Problem HDA Intel ALC883 Low Volume"
date: 2009-07-19
forum: Multimedia Software
---

### Post by jpt266 on 2009-07-19
I have poor audio volume. It is muted, not loud enough. I have looked, read, and tried many ideas. I have some computer experience.

Can somebody point me in the right direction? I have tried to list some useful info.

Thanks,

john@john-linux:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

john@john-linux:~$ lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
01:00.0 Ethernet controller: Attansic Technology Corp. L1e Gigabit Ethernet Adapter (rev b0)

---

### Post by igorzwx on 2009-07-19
it is OSS4, but try something similar
[http://wiki.archlinux.org/index.php/OSS#Troubleshooting_HDAudio_devices](http://wiki.archlinux.org/index.php/OSS#Troubleshooting_HDAudio_devices)

---

### Post by ajgreeny on 2009-07-19
Have you made sure everything in alsamixer is set at a high enough level?  In the normal volume control showing on the panel, there are a lot of hidden channels which you may need to enable in order to make sure things are correct, or just use ```
alsamixer
``` in terminal to see everything possible.

---

### Post by jpt266 on 2009-07-19
Yes to alsamixer and tried OSS4. I am just a computer enthusiast. I tinker with the OS. I have had Ubuntu 9.04 working on a different box (motherboard) but this does not work right. It is an ASUS P5QL-AM motherboard. But I am getting close to giving up on this one.

Keep trying!

---

### Post by jpt266 on 2009-08-01
My system came to life. I have read posts saying that MS Windows and/or Vista has had a influence on Linux audio. On my system I loaded Win7 then went back to Ubuntu 9.04 and wa-la, sound is here.

I do not have the answers but many, many people have posted about audio problems. Me too. It seems something that effects the BIOS.

---

