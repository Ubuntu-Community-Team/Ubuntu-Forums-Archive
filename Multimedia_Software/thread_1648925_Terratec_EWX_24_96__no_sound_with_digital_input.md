---
title: "Terratec EWX 24 96 : no sound with digital input"
date: 2010-12-19
forum: Multimedia Software
---

### Post by jimiyves on 2010-12-19
Hi everyone,


I'm using a terratec EWX 24 96 sound card with ubuntu studio, and I have sound with the digital output, I have no sound with the digital input.

I had sound with the same configuration in Windows XP, and all the hardware is ok.

I think I have no sound at all, with Ardour or Rosegarden, that's like if the digital input was not here in jack.

Could someone help me please ?

Thanks.

---

### Post by cchhrriiss121212 on 2010-12-19
Hi
Could you post your jack settings? (just type cat ~/.jackdrc in a terminal)
And also the result of this from a terminal:
arecord -l

---

### Post by jimiyves on 2010-12-19
Jack settings :

[http://img526.imageshack.us/img526/8535/capturell.png](http://img526.imageshack.us/img526/8535/capturell.png)

The result of arecord -l :

(in french)

```
carte 0: EWX2496 [TerraTec EWX24/96], périphérique 0 : ICE1712 multi [ICE1712 multi]
Sous-périphérique: 0/1
Sous-périphérique: #0: subdevice #0 
```

---

### Post by cchhrriiss121212 on 2010-12-19
Try shutting down jack and Ardour for the time being, then open up envy24control and take a look at the monitor inputs tab. 
Send a constant stream through the digital inputs and see if you get any movement.

---

### Post by jimiyves on 2010-12-20
I have no movement.

---

### Post by cchhrriiss121212 on 2010-12-20
So this shows the system does not recognize your digital input for some reason. I have no experience with this card, but the ALSA database states that it has full support for digital in and out. I would double check your input signal with XP (if you still have it handy).

If you are sure of the signal, could you tell me how many inputs you see available in envy24?

---

### Post by jimiyves on 2010-12-20
I'm sure the signal is OK since it worked with XP.

In envy24 I see 4 inputs : H/W In 1, H/W In 2, SPDIF In L, SPDIF In R.

---

### Post by cchhrriiss121212 on 2010-12-20
>  		I'm sure the signal is OK since **it worked** with XP
To clarify: Does it work right now or did it work a year ago or something?
The reason I ask is that this card has a jumper switch on the board that controls digital input. From the manual:
> On the EWX 24/96 board there is a pin connector with accompanying jumper. With
this jumper you can set an external S/PDIF signal with the so-called TTL level, which
most CD ROM drives send in. This jumper determines which digital port on the card is
active – either the externally accessible optical interface, or the internal one men-
tioned here. Simultaneous use of both connectors is not possible.
Jumper Settings and Internal Digital Connections.
J1, sets the Digital Input Source:
        1-2 &#8594; External Input (optical)
        2-3 &#8594; Internal Input (TTL or S/PDIF electrical)
J2, sets the Internal Digital Source Format:
        Open &#8594; CD-ROM audio, TTL level
        Closed &#8594; S/PDIF electrical
J9, Internal Digital Input (CD-ROM Audio, TTL level)
J10, Internal Digital Output (S/PDIF electrical)
This is worth a check.

---

### Post by jimiyves on 2010-12-20
It was working just before I install Ubuntu. I did not move the jumpers when I installed Ubuntu.

---

### Post by jimiyves on 2010-12-22
No other idea ? Do you think it must be a hardware matter ?

---

### Post by cchhrriiss121212 on 2010-12-22
> Do you think it must be a hardware matter ?
I don't know, what I do know is that your card is fully supported by ALSA, and AFAIK ALSA does not suffer from regressions like this. I can't find any user reports of digital input either working or not working on this card.

I still recommend you try the jumper switch, it might be that Linux requires it to be in the other position, or it may just need to be reset to the same position, I have had stranger things happen with audio hardware.

Or it could be that you have a newer revision of the EWX 24/96 which may cause minor issues as the driver was designed for an older revision.

---

### Post by jimiyves on 2010-12-22
Thank you for your answer, I will do other tests.

---

### Post by tomfool on 2010-12-26
Hi,
I'm trying to work it out too,but i didn't do it.
Do you?
I'm using ubuntu 9.10 alsa 1.20.
Thanks!

---

### Post by jimiyves on 2010-12-29
Hi,

It is working now ! It was a hardware matter indeed, but not a matter with the soundcard, a matter with a AD/DA converter.

Thank you for your help.

tomfool > my card is fully working now, with Ubuntu 10.04 and Ubuntu studio 10.04. What is not working with your computer ?

---

### Post by tomfool on 2010-12-30
Hi jimi,
Well no sound from jack,did you make something for getting it work out?if yes could you explain what,because i'm getting mad!:-)

---

### Post by jimiyves on 2010-12-30
You can do what told cchhrriiss121212 in this topic.

---

### Post by tomfool on 2010-12-30
Could you please tell me what you did step by step,i'll be glad of it!:)

---

### Post by tomfool on 2011-01-05
Up please...!!

---

### Post by cchhrriiss121212 on 2011-01-05
Tomfool, please post the following outputs from a terminal window:
aplay -l && arecord -l && lspci -v && cat ~/.jackdrc

Also please verify what problem you are having.

---

### Post by tomfool on 2011-01-06
Here it is!
I don't have any kinda sound comes out from sound card.therefore Envy24 control doesn't show any signal.
thanks



> scheda 1: EWX2496 [TerraTec EWX24/96], dispositivo 0: ICE1712 multi [ICE1712 multi]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
**** Lista di CAPTURE dispositivi hardware ****
scheda 1: EWX2496 [TerraTec EWX24/96], dispositivo 0: ICE1712 multi [ICE1712 multi]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
00:00.0 Host bridge: VIA Technologies, Inc. PT880 Ultra/PT894 Host Bridge
    Subsystem: ASRock Incorporation Device 0308
    Flags: bus master, medium devsel, latency 8
    Memory at f8000000 (32-bit, prefetchable) [size=64M]
    Capabilities: <access denied>
    Kernel driver in use: agpgart-via
    Kernel modules: via-agp

00:00.1 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
    Subsystem: ASRock Incorporation Device 1308
    Flags: bus master, medium devsel, latency 0

00:00.2 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
    Subsystem: ASRock Incorporation Device 2308
    Flags: bus master, medium devsel, latency 0

00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
    Flags: bus master, medium devsel, latency 0
    Kernel modules: via-agp

00:00.4 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
    Subsystem: ASRock Incorporation Device 4308
    Flags: bus master, medium devsel, latency 0

00:00.5 PIC: VIA Technologies, Inc. PT894 I/O APIC Interrupt Controller (prog-if 20)
    Subsystem: ASRock Incorporation Device 5308
    Flags: bus master, fast devsel, latency 0

00:00.7 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
    Flags: bus master, medium devsel, latency 0

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
    Flags: bus master, 66MHz, medium devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    Memory behind bridge: ff300000-ff3fffff
    Capabilities: <access denied>
    Kernel modules: shpchp

00:02.0 PCI bridge: VIA Technologies, Inc. PT890 PCI to PCI Bridge Controller
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00009000-0000bfff
    Memory behind bridge: ff400000-ff4fffff
    Prefetchable memory behind bridge: bff00000-dfefffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:0a.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
    Subsystem: TERRATEC Electronic GmbH Device 1130
    Flags: bus master, medium devsel, latency 32, IRQ 18
    I/O ports at d000 [size=32]
    I/O ports at cc00 [size=16]
    I/O ports at c880 [size=16]
    I/O ports at c800 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: ICE1712
    Kernel modules: snd-ice1712

00:0f.0 RAID bus controller: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
    Subsystem: ASRock Incorporation Device 0591
    Flags: bus master, medium devsel, latency 32, IRQ 21
    I/O ports at ec00 [size=8]
    I/O ports at e880 [size=4]
    I/O ports at e800 [size=8]
    I/O ports at e480 [size=4]
    I/O ports at e400 [size=16]
    I/O ports at e000 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sata_via
    Kernel modules: sata_via

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07) (prog-if 8a [Master SecP PriP])
    Subsystem: ASRock Incorporation Device 0571
    Flags: bus master, medium devsel, latency 32
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
    I/O ports at fc00 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_via
    Kernel modules: pata_via

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
    Subsystem: ASRock Incorporation Device 3038
    Flags: bus master, medium devsel, latency 32, IRQ 20
    I/O ports at d080 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
    Subsystem: ASRock Incorporation Device 3038
    Flags: bus master, medium devsel, latency 32, IRQ 22
    I/O ports at d400 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
    Subsystem: ASRock Incorporation Device 3038
    Flags: bus master, medium devsel, latency 32, IRQ 21
    I/O ports at d480 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
    Subsystem: ASRock Incorporation Device 3038
    Flags: bus master, medium devsel, latency 32, IRQ 23
    I/O ports at dc00 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20)
    Subsystem: ASRock Incorporation Device 3104
    Flags: bus master, medium devsel, latency 32, IRQ 21
    Memory at ff6ff800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
    Subsystem: ASRock Incorporation Device 3337
    Flags: medium devsel
    Capabilities: <access denied>
    Kernel modules: i2c-viapro

00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
    Subsystem: VIA Technologies, Inc. Device 337e
    Flags: bus master, medium devsel, latency 32
    Capabilities: <access denied>

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
    Subsystem: ASRock Incorporation Device 3065
    Flags: bus master, medium devsel, latency 32, IRQ 23
    I/O ports at d800 [size=256]
    Memory at ff6ffc00 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: via-rhine
    Kernel modules: via-rhine

00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
    Flags: bus master, fast devsel, latency 0

02:00.0 VGA compatible controller: ATI Technologies Inc RV515 [Radeon X1300]
    Flags: bus master, fast devsel, latency 0, IRQ 24
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at ff4f0000 (64-bit, non-prefetchable) [size=64K]
    I/O ports at b000 [size=256]
    Expansion ROM at ff4c0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel modules: radeon

02:00.1 Display controller: ATI Technologies Inc RV515 [Radeon X1300] (Secondary)
    Flags: bus master, fast devsel, latency 0
    Memory at ff4e0000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>

/usr/bin/jackd -p 128 -R -P 60 -T -d alsa -n 2 -r 48000 -p 1024 -d hw:0,0 
 

---

### Post by cchhrriiss121212 on 2011-01-07
That output looks OK to me, have you checked that your volume levels are high enough? Use the Analogue Volume tab in envy24control.

ADC means input level and DAC means output level.

---

### Post by tomfool on 2011-01-07
I'll check!Thanks chris!i'm gotta let you know!
Do i have to set any option in alsa.conf?

---

