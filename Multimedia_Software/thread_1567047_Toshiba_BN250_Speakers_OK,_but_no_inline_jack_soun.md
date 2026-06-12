---
title: "Toshiba BN250 Speakers OK, but no inline jack sound"
date: 2010-09-03
forum: Multimedia Software
---

### Post by pierreu1 on 2010-09-03
I am a new user, so please bear with me.

I have installed the newest version of Ubuntu (I am not sure what is the name of this version) and installation went well. I have noticed though that while speakers do work well, my in line jack connection for my older cyber acoustics headset is not working at all. I have tried to find a solution to this problem for the last 2 days as most users would, but to no avail. I have unmuted all sound parameters in my sound preferences and check if the alsa mixer was set properly. I have upgrade and updated everything as per forum's advice.

I have copied below the results from a list of commands that might help forum members help me (as another thread advised). This is mostly Chinese to me, so I will let the pros help me.

Let me know if you need more info.

janey@janey-laptop:~$ aplay-l
aplay-l: command not found
janey@janey-laptop:~$ cat /proc/asound/modules
 0 snd_hda_intel
janey@janey-laptop:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf0300000 irq 22
janey@janey-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
07:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
janey@janey-laptop:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf0300000 irq 22
janey@janey-laptop:~$ cat /proc/asound/modules
 0 snd_hda_intel
janey@janey-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
janey@janey-laptop:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
janey@janey-laptop:~$ 

Thanks for the help.

P.

PS: This is my wife's laptop, if it matters at all. :)

---

### Post by pierreu1 on 2010-09-04
Made an unfortunate error when typing the model number of the Toshiba netbook. It is actually:

NB250. This was bought in Asia (Thailand).

I realize that I could edit the title as well, so I have made the change everywhere I could.

So sorry for the confusion!

---

### Post by pierreu1 on 2010-09-04
Looked for some threads on headphones and found the solution here:[ http://playingwithsid.blogspot.com/2010/06/headphone-jack-sense-problem-in-ubuntu.html]("http://playingwithsid.blogspot.com/2010/06/headphone-jack-sense-problem-in-ubuntu.html") as reported in a different post [http://ubuntuforums.org/showthread.php?t=1470643&highlight=headphone](http://ubuntuforums.org/showthread.php?t=1470643&highlight=headphone) . I just followed the instruction of/in the first link. 

Thanks for the help and let's hope this helps others as well.

---

### Post by chesterlinux on 2010-10-03
I am having the same issue, but I think these posts do not help.  The issue isn't that the sound from the speakers and the headphone jack work at the same time and you can't turn one off or the other when either is in operation... It's that the head phone jack doesn't work at all when you plug external speakers into the computer there is nothing that works.  Only the internal speakers work.  PLEASE HELP!

---

### Post by garvint on 2011-02-27
I too have the same problem, and cannot figure out how to get audio out of earphone socket.

Has anyone solved this problem yet for Ubuntu users?

---

