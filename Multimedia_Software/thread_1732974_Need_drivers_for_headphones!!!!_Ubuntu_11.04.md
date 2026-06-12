---
title: "Need drivers for headphones!!!! Ubuntu 11.04"
date: 2011-04-18
forum: Multimedia Software
---

### Post by Nichijou on 2011-04-18
hi!, i was tryng to listen some music with da headphones , but i realise that it doesnt work . I think that are the drives , so i need one !!! please helpppppp!!!!

 
> AlsaMixer v1.0.24.2

> 
 Card: HDA ATI SB                                     F1:  Help              
 Chip: Realtek ALC861-VD                              F2:  System information 
 View: F3:[Playback] F4: Capture  F5: All             F6:  Select sound card  
 Item: Master [dB gain: 0.00, 0.00]                   Esc: Exit              

---

### Post by lidex on 2011-04-18
What is the make and model of this comp?

---

### Post by Nichijou on 2011-04-18
Packard Bell Easynote MZ375

---

### Post by lidex on 2011-04-18
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model= 
```
Save. Close. Reboot. 
Check your levels in alsamixer.

Your options are the model names in the left column here:
```
ALC861VD/660VD
==============
  3stack        3-jack
  3stack-dig    3-jack with SPDIF OUT
  6stack-dig    6-jack with SPDIF OUT
  3stack-660    3-jack (for ALC660VD)
  3stack-660-digout 3-jack with SPDIF OUT (for ALC660VD)
  lenovo        Lenovo 3000 C200
  dallas        Dallas laptops
  hp            HP TX1000
  asus-v1s      ASUS V1Sn
  auto          auto-config reading BIOS (default)

```
Put it directly after the = (no space) and reboot or reload alsa to initialize the changes.

---

### Post by Nichijou on 2011-04-22
Thanks!!! Itwas the hp one!!!! :D

---

### Post by rohitprabhakar on 2011-11-02
> **lidex said:**
> Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model= 
```
Save. Close. Reboot. 
Check your levels in alsamixer.

Your options are the model names in the left column here:
```
ALC861VD/660VD
==============
  3stack        3-jack
  3stack-dig    3-jack with SPDIF OUT
  6stack-dig    6-jack with SPDIF OUT
  3stack-660    3-jack (for ALC660VD)
  3stack-660-digout 3-jack with SPDIF OUT (for ALC660VD)
  lenovo        Lenovo 3000 C200
  dallas        Dallas laptops
  hp            HP TX1000
  asus-v1s      ASUS V1Sn
  auto          auto-config reading BIOS (default)

```
Put it directly after the = (no space) and reboot or reload alsa to initialize the changes.



Dear

I have the Dell Laptop kindly suggest the last option

---

### Post by rohitprabhakar on 2011-11-02
Dear 

I am facing the same problem 

Laptop speakers are working but not the headphones when pluged in

kindly suggest

---

### Post by lisati on 2011-11-02
Time for the thread to go back to sleep. 

@rohitprabhakar: Please start your own thread

---

