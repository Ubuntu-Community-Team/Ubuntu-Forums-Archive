---
title: "Sound turns into noise....."
date: 2009-04-03
forum: Multimedia Software
---

### Post by thornpig on 2009-04-03
Every morning when I arrive at my office,I find the sound of my office computer, which was perfect the day before at least until I left off work,has turned into noise. Then I have to re-login to the system to get the sound back. This is effective to restore the sound, but my other running programs are terminated meanwhile. I can kill the pulseaudio but I can't restart it(The error messages are shown below).Please help me out with this annoying problem.Thanks in advance!

OS version: intrepid

pulseaudio restart error:
zhuzd@esge6ea:~$ killall pulseaudio
zhuzd@esge6ea:~$ sudo pulseaudio -D
[sudo] password for zhuzd: 
W: ltdl-bind-now.c: Failed to find original dlopen loader.
E: main.c: daemon startup failed


Other system information:
zhuzd@esge6ea:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 0a)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 0a)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 0a)
00:02.1 Display controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 0a)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA AHCI Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787 Gigabit Ethernet PCI Express (rev 02)
zhuzd@esge6ea:~$ lsusb
Bus 005 Device 005: ID 059f:1012 LaCie, Ltd 
Bus 005 Device 003: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
zhuzd@esge6ea:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xdfdfc000 irq 16
zhuzd@esge6ea:~$ cat /proc/asound/modules
 0 snd_hda_intel
zhuzd@esge6ea:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
zhuzd@esge6ea:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

---

### Post by bertolo on 2009-04-06
try this:
open volume control, preferences, enable all the xit there. put volume in max in all parameters.
then in switches choose headphones and disable the other two options below.
ps:select HDA intel drivers.
this was my solution when i had the same problem

---

### Post by thornpig on 2009-04-08
Thanks a lot for  you reply.The sound has been working properly since I posted this thead, which is wierd because i did nothing to fix it. Anyway, i'll try your solution next time the noise comes.

---

