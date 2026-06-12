---
title: "Jack not showing up audio interface that it used to show up?"
date: 2010-09-30
forum: Multimedia Software
---

### Post by Macfunky on 2010-09-30
I have an Alesis multimix 12 which i have used in previous versions of Ubuntu. Haven't used it in awhile and yesterday was my first time sitting down with 10.04 and the interface. I opened up jack and went to set it as my interface but no sign of it. It used to show up as something with USB in the title. I cannot find that anymore and it's annoying me cause it used to work perfectly. None of the options are it as i have tried them all. How do i get it to recognize my interface like previous versions did automatically?

---

### Post by cchhrriiss121212 on 2010-09-30
Is this the firewire or USB version?

---

### Post by Macfunky on 2010-09-30
> **cchhrriiss121212 said:**
> Is this the firewire or USB version?

USB version. It worked automatically in previous versions of Ubuntu. Here is the output from the terminal for lsusb

conor@JuneBug:~$ lsusb
Bus 004 Device 004: ID 08bb:2902 Texas Instruments Japan 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1bcf:0007 Sunplus Innovation Technology Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
conor@JuneBug:~$ 

Texas Instruments Japan is the interface so it is being recognized by ubuntu. It is not showing up in Jack though. Any ideas on how i can get it showing up there?

---

### Post by cchhrriiss121212 on 2010-09-30
Do you get anything with aplay -l or arecord -l?

---

### Post by Macfunky on 2010-09-30
> **cchhrriiss121212 said:**
> Do you get anything with aplay -l or arecord -l?

The output from those -

conor@JuneBug:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [USB Audio CODEC ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
conor@JuneBug:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 1: Intel ICH - MIC ADC [Intel ICH5 - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 2: Intel ICH - MIC2 ADC [Intel ICH5 - MIC2 ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 3: Intel ICH - ADC2 [Intel ICH5 - ADC2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [USB Audio CODEC ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
conor@JuneBug:~$ 

So I've been messing about and the interface is working. I found it in sound preferences and have it set to both input and output. I have recorded my voice in audacity and played music from banshee so it's working fine. It's still not showing up in Jack.

---

### Post by cchhrriiss121212 on 2010-09-30
It seems to be hw:1, do you get any options for that in qjackctl? If not try typing in hw:1 and pressing start.

---

### Post by Macfunky on 2010-09-30
> **cchhrriiss121212 said:**
> It seems to be hw:1, do you get any options for that in qjackctl? If not try typing in hw:1 and pressing start.

Thank you very much. That has it working now :D

---

