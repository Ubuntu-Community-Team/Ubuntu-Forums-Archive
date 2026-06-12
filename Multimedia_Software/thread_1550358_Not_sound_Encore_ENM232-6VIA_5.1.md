---
title: "Not sound Encore ENM232-6VIA 5.1"
date: 2010-08-10
forum: Multimedia Software
---

### Post by Tres_Iqus on 2010-08-10
OS: ubuntu 10.04 new install
Please HELP 

#lshw
*-multimedia
                description: Multimedia audio controller
                product: VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller
                vendor: VIA Technologies Inc.
                physical id: 6
                bus info: pci@0000:03:06.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ICE1724 latency=64
                resources: irq:21 ioport:cf00(size=32) ioport:ce00(size=128)

#lspci
03:06.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)

#cat /proc/asound/cards
 0 [ICE1724        ]: ICE1724 - ICEnsemble ICE1724
                      ICEnsemble ICE1724 at 0xcf00, irq 21

#aplay -l
**** Lista de PLAYBACK dispositivos hardware ****
tarjeta 0: ICE1724 [ICEnsemble ICE1724], dispositivo 0: ICE1724 [ICE1724]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: ICE1724 [ICEnsemble ICE1724], dispositivo 1: ICE1724 IEC958 [ICE1724 IEC958]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

aplay -L
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=ICE1724,DEV=0
    ICEnsemble ICE1724, ICE1724
    Front speakers
surround40:CARD=ICE1724,DEV=0
    ICEnsemble ICE1724, ICE1724
    4.0 Surround output to Front and Rear speakers
surround41:CARD=ICE1724,DEV=0
    ICEnsemble ICE1724, ICE1724
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=ICE1724,DEV=0
    ICEnsemble ICE1724, ICE1724
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=ICE1724,DEV=0
    ICEnsemble ICE1724, ICE1724
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=ICE1724,DEV=0
    ICEnsemble ICE1724, ICE1724
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=ICE1724,DEV=0
    ICEnsemble ICE1724, ICE1724
    IEC958 (S/PDIF) Digital Audio Output


#dmesg
[    9.608906] ICE1724 0000:03:06.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    9.646838] ice1724: No matching model found for ID 0x12140324
[    9.649770] ice1724: Invalid EEPROM version 1

#uname -a
Linux srvcga 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 i686 GNU/Linux

---

### Post by kostkon on 2010-08-11
Did you try to setup your sound in System &#8594; Preferences &#8594; Sound?

---

### Post by Tres_Iqus on 2010-08-12
yes and not sound =(

---

### Post by lidex on 2010-08-14
Start reading:
[http://www.google.com/search?hl=en&newwindow=1&safe=off&sitesearch=ubuntuforums.org&&sa=X&ei=S6xmTLjXCdOknQeepYjBBQ&ved=0CBQQBSgA&q=ice1724&spell=1](http://www.google.com/search?hl=en&newwindow=1&safe=off&sitesearch=ubuntuforums.org&&sa=X&ei=S6xmTLjXCdOknQeepYjBBQ&ved=0CBQQBSgA&q=ice1724&spell=1)
What is the make/model of this unit?
That eeprom error is new to me. What do you get as output for this:
```
dmesg | grep firmware
```
These also:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

---

