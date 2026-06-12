---
title: "Rocketfish PCI 7.1 Audio Drivers (have cd)"
date: 2009-07-20
forum: Multimedia Software
---

### Post by william_hunter on 2009-07-20
Hey all. Ubuntu thinks this sound card is a SB Audigy LS, and it wont work. I do have the original driver disk. Help?

Here is the output from my examination of the PCI devices on the system:

```

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
01:01.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
03:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ cat /proc/asound/cards
 0 [CA0106         ]: CA0106 - CA0106
                      AudigyLS [Unknown] at 0xc800 irq 21
ubuntu@ubuntu:~$ cat /proc/asound/modules
 0 snd_ca0106
ubuntu@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ubuntu@ubuntu:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Thanks in advance to anyone that can help me with this..I switched this machine to Ubuntu from windows because windows wouldn't work well for more than a day with the build I have..annoying.

---

### Post by zetanuxi on 2009-07-21
I have the same card for my media center. With a fresh install of Jaunty, the card worked fine. I didn't have to install any drivers manually. I only run out if the optical port, so I'm guessing if that works then the other ports work too. 

The card does have an SB Audigy LS chipset. Look on the card itself. Read the label on the big chip. Using those drivers is the only way the card will work. I've tried everything else. I just found it better to leave it with that. Plays 5.1 and ACC no problem.

The CD drivers aren't worth a thing. I burned that CD in the grill. It was more useful that way. :D

---

### Post by Stanzaman on 2009-12-06
Now, I have this same card, and yes it does seem to have surround capability via the analog ports, but am I just crazy, or does the optical port not support surround?  I'm running version 9.10, and it gives me an option to choose between either 7.1 analog surround, or Optical stereo.  My old reciever has no method of receiving analog surround sound, but it does have an optical in for 5.1 surround.  All I can ever get out of it though are the center, and left/right front channels.

---

### Post by Vance Gilbert on 2011-10-27
I have the soundcard installed, and it worked just recently until I upgraded Ubuntu from 10.4 to 10.4.3

Now the sound card has a very annoying static sound whenever there's supposed to be a sound file played. (Music and videos don't play either.)

Could someone please tell me how to install the sound card driver to fit a Rocketfish 5.1 pci soundcard? (a.k.a. Soundblaster Audigy LS)

Thank you in advance for your assistance, it's appreciated.

---

