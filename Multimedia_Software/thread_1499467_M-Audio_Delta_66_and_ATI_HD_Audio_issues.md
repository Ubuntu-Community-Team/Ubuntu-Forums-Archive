---
title: "M-Audio Delta 66 and ATI HD Audio issues"
date: 2010-06-01
forum: Multimedia Software
---

### Post by slayer8322 on 2010-06-01
Hello, I am having some issues with getting Ubuntu Studio 10.04 to work correctly on my system.  Everything works fine except sound.  I have a M-Audio Delta 66 audio interface and my onboard sound is disabled.  When I run the command alsaconf I can see the ICE1712 card without issue.  However when I run alsamixer the only option it is giving me is my HD sound from my ATI video card.  For some reason it seems the ATI card has locked the audio to it with no way to remove it.  I have reinstalled the alsa drivers for my card and can only see it through alsaconf.  When I tell alsaconf to configure the ICE1712 card it says it configured it properly.  
 
When I run the command envy24control it says no ICE1712 cards were found.
 
Any Ideas.
 
Thanks,
Dusty

---

### Post by cchhrriiss121212 on 2010-06-02
Did you disable the onboard card from BIOS or by using blacklist?
Could you post what aplay -l and lspci show?

---

### Post by slayer8322 on 2010-06-02
The onboard sound is disabled.  i will post the results of those commands as soon as I get home.  I am not really use to dealling with audio on a video card and I am wandering if that may be what is causing issues.  Will post again soon.

---

### Post by slayer8322 on 2010-06-02
Output of command aplay -l is  
card 1: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

---

### Post by slayer8322 on 2010-06-02
lspci shows 


00:00.0 Host bridge: ATI Technologies Inc RD790 Northbridge only dual slot PCI-e_GFX and HT3 K8 part
00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
00:04.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port A)
00:05.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port B)
00:07.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port D)
00:09.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port E)
00:0a.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port F)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc Device 6898
01:00.1 Audio device: ATI Technologies Inc Cypress HDMI Audio [Radeon HD 5800 Series]
02:00.0 USB Controller: NEC Corporation Device 0194 (rev 03)
03:00.0 IDE interface: Device 1b4b:91a3 (rev 11)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
06:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
06:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
07:07.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
07:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

---

### Post by cchhrriiss121212 on 2010-06-02
Could you try this:
```
sudo modprobe snd-ice1712
```
And then try aplay -l again. I'm following the instructions on [this thread]("http://ubuntuforums.org/showthread.php?t=205449") btw, and if it doesn't work I would try to lookup how to blacklist your ATI sound module.

---

### Post by slayer8322 on 2010-06-05
Sorry for the wait,  I run the command you asked and got this


dusty@slayerpc:~$ sudo modprobe snd-ice1712
WARNING: Error inserting snd_ak4xxx_adda (/lib/modules/2.6.32-22-preempt/updates/alsa/i2c/other/snd-ak4xxx-adda.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_ice17xx_ak4xxx (/lib/modules/2.6.32-22-preempt/updates/alsa/pci/ice1712/snd-ice17xx-ak4xxx.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_ice1712 (/lib/modules/2.6.32-22-preempt/kernel/sound/pci/ice1712/snd-ice1712.ko): Unknown symbol in module, or unknown parameter (see dmesg)
dusty@slayerpc:~$

---

### Post by slayer8322 on 2010-06-05
Just so everyone that reads this knows.  I have a rev. E card.  It shows up as a rev 2.  I have read that this card has issue with alsa and it is related to the SP/DIF's not working.  Do you all know how I can modify the driver to not load the cs8427 chips?

---

### Post by Yellow Pasque on 2010-06-05
Try installing update ALSA kernel modules (and rebooting or reloading alsa). It might be fixed: [http://www.alsa-project.org/main/index.php/Changes_v1.0.21_v1.0.22#AK4XXX_AD.2FDA_converters_2](http://www.alsa-project.org/main/index.php/Changes_v1.0.21_v1.0.22#AK4XXX_AD.2FDA_converters_2)
```
sudo apt-get install linux-backports-modules-alsa-lucid-generic
```

---

### Post by slayer8322 on 2010-06-19
I will try that when I get home today.  Sorry about being away for a bit.  It is crazy at work.  I really appreciate all of your alls help.  I hope this fixes it.  I am not for sure what to try next.  I am hoping alsa has/or will fix this issue.  I am at the point now of thinking about swapping out my 66 for a older 44 to get the original rev of the card so it will work without issue.  I will post back what happens.

---

### Post by MIJ-VI on 2010-06-28
> **slayer8322 said:**
> Hello, I am having some issues with getting Ubuntu Studio 10.04 to work correctly on my system.  Everything works fine except sound.  I have a M-Audio Delta 66 audio interface and my onboard sound is disabled.  When I run the command alsaconf I can see the ICE1712 card without issue.  However _when I run alsamixer the only option it is giving me is my HD sound from my ATI video card_.  For some reason it seems the ATI card has locked the audio to it with no way to remove it.  I have reinstalled the alsa drivers for my card and can only see it through alsaconf.  When I tell alsaconf to configure the ICE1712 card it says it configured it properly.  
 
When I run the command envy24control it says no ICE1712 cards were found.
 
Any Ideas.
 
Thanks,
Dusty

Hi Dusty.

Re alsamixer. Did you try F6:  Select sound card?

---

