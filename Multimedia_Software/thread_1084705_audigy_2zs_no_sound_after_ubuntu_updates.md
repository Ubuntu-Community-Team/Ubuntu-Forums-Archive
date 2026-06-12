---
title: "audigy 2zs no sound after ubuntu updates"
date: 2009-03-02
forum: Multimedia Software
---

### Post by phoenix5211 on 2009-03-02
I am running intrepid ibex. As long as I don't update Ubuntu my soiund is fine. If I try to run an up dated version I have no sound. I have tried disabeling pulse audio, I have even gone so far as to rip it out completely.  it made no difference. I re installed the sound drivers and have made sure I have the proper ones for the card. Any help would be appreciated as this is driving me insane.

---

### Post by mc4man on 2009-03-02
You need to switch off the "Audigy Analog/Digital Output Jack"

Easiest way - double left click on little speaker icon in upper panel, if you see a tab 'switches' open it and uncheck the switch.
If a switches tab isn't there then click on 'preferences', scroll down and enable the "Audigy Analog/Digital Output Jack" switch and then go back to 'Switches' and disable.

---

### Post by phoenix5211 on 2009-03-02
> **mc4man said:**
> You need to switch off the "Audigy Analog/Digital Output Jack"

Easiest way - double left click on little speaker icon in upper panel, if you see a tab 'switches' open it and uncheck the switch.
If a switches tab isn't there then click on 'preferences', scroll down and enable the "Audigy Analog/Digital Output Jack" switch and then go back to 'Switches' and disable.
Already tried that, thanx for the help though.

---

### Post by markbuntu on 2009-03-03
Please post the output of the following

lspci

aplay -l

cat /proc/asound/cards

cat /proc/asound/modules

---

### Post by Blind Tiger on 2009-05-06
This setting change worked for me!  Thanks.

re: Volume Control --> Switches --> uncheck Audigy Analog/Digital Output Jack

---

### Post by phoenix5211 on 2009-05-07
> **markbuntu said:**
> Please post the output of the following

lspci

aplay -l

cat /proc/asound/cards

cat /proc/asound/modules
Just switched to Jaunty, I have sound but none in my rear speakers. I have even removed my audigy and gone to the onboard sound which is realtek. Still nothing in my rear channels. here is the requested information:
 
lspci:  queen@queen-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV36.2 [GeForce FX 5700] (rev a1)
02:05.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
02:09.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
02:09.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)

 
aplay -l: **** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

cat /proc/asound/cards:  0 [ICH5           ]: ICH4 - Intel ICH5
                      Intel ICH5 with ALC850 at irq 17
 1 [Bt878          ]: Bt87x - Brooktree Bt878
                      Brooktree Bt878 at 0xf7eff000, irq 21



cat /proc/asound/modules: 0 snd_intel8x0
 1 snd_bt87x

---

