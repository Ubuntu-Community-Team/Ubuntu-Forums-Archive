---
title: "CMI8768 driver"
date: 2006-02-22
forum: Multimedia &amp; Video
---

### Post by Artanis on 2006-02-22
I've googled a fair bit looking for a driver for my onboard  CMI8768 chipset, OSS says to include this driver but I can't get it to install (installer says it cannot remove ALSA drivers, which is werid because i removed linux-sound-base and everything else I could find that related to alsa).

Was hoping that somone here could shed a light on what I can do to fix my probelm. 

```
$ cat /proct/asound/cards
0 [CMI8738MC8     ]: CMI8738-MC8 - C-Media PCI CMI8738-MC8
                     C-Media PCI CMI8738-MC8 (model 68) at 0xc100, irq 16
```
Thats the driver Breezy installed for my card. Vendor is right.. just not model 8(

Anything else that is needed I can post here.

Thanks for any help that you guys give me, hopefully somone in the know can help me with this ;)

---

### Post by Artanis on 2006-02-28
So there isnt anyone willing to give me a hand on this one? I've tried installing the nForce drivers (Motherboard is nForce 3 250) but they didn't help either..

---

### Post by ransombot on 2006-10-26
ALSA won't aparently properly detect this card in the 2.6* kernel.. I have had it working in the 2.4 kernel usualy it's auto detected properly. in 2.6 it shows up as an improper 87* card


```

root@mythtv:~/src/alsaconf-0.4.3b# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: CMI8738MC8 [C-Media PCI CMI8738-MC8], device 0: CMI8738-MC8 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: CMI8738MC8 [C-Media PCI CMI8738-MC8], device 1: CMI8738-MC8 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: CMI8738MC8 [C-Media PCI CMI8738-MC8], device 2: CMI8738-MC8 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
```

root@mythtv:~/src/alsaconf-0.4.3b# lspci |grep CM
0000:00:11.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)

```

not sure if there is a way to fix it.. me.. I'm going back to my on board audio that works in 2.6 but not 2.4 *shake* fun stuff!

If someone else has some input on how to get it working properly though I'd be more tha happy to hear aswell ](*,)

---

