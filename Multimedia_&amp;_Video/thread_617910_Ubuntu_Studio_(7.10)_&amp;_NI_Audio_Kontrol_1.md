---
title: "Ubuntu Studio (7.10) &amp; NI Audio Kontrol 1"
date: 2007-11-19
forum: Multimedia &amp; Video
---

### Post by noesis on 2007-11-19
I just installed Ubuntu Studio, and am trying to get my external USB Audio Kontrol 1 audio card to work. However, nothing happens. Neither the USB card nor the internal sound card is working. I found a solution as to the internal sound card, although I cannot find any solution to the Native Instruments specific problem. Is it possible at all to get this audio card to work in Ubuntu Studio?

Some outputs:

```
cat /proc/asound/cards
```
0 [A1             ]: snd-usb-caiaq - Audio Kontrol 1
                      Native Instruments Audio Kontrol 1 (serial SN-SN-XXXXXXX  
                      usb-0000:00:1d.7-1)
 1 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf8400000 irq 20

```
cat /proc/asound/modules
```
0 snd_usb_caiaq
 1 snd_hda_intel

```
aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: A1 [Audio Kontrol 1], device 0: Audio Kontrol 1 [Audio Kontrol 1]
  Subdevices: 0/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 1: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
sudo lshw -C sound
```
*-multimedia            
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

---

### Post by deadgobby on 2007-11-19
[http://www.native-instruments.com/forum_us/archive/index.php/t-53898.html](http://www.native-instruments.com/forum_us/archive/index.php/t-53898.html)

Gobby

---

### Post by noesis on 2007-11-20
Thank you for the link. Too bad that this won't work, despite the kernel modules specifically aimed at this hardware. 

Regards,

noesis

---

### Post by the_prophet on 2008-03-12
I think you should have a look at this [NI  forum post]('http://www.native-instruments.com/forum/showpost.php?p=384983&postcount=7).

PS: Official Ubuntu forums suck!

---

