---
title: "USB audio interface Edirol 1 not working"
date: 2009-11-01
forum: Multimedia Software
---

### Post by sojournerC on 2009-11-01
I have a USB soundcard/midi controller that I would like to use. Plugged in, the midi functions with jack and software synths, but the soundcard does not appear in preferences>sound. 

How do I get the card to be recognized so that I may use it in jack instead of the onboard card?

It is recognized in the usb port via lsusb
************************
[COLOR=Red]Bus 005 Device 004: ID 0582:0064 Roland Corp. EDIROL PCR-1 WAVE
Bus 005 Device 003: ID 0582:0065 Roland Corp. EDIROL PCR-1 MIDI[/COLOR]
****************************
but it isn't in aplay -l
***********************
chris@chris-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: SB [HDA ATI SB], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
***************************

Thanks for your help.

---

### Post by Hanine on 2010-10-02
I have the same problem.
My Device is an Audio Interface :

Edirol UA-25 USB.

Upon : lsusb ---->

```
$ lsusb
```
Bus 005 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 0603:00f2 Novatek Microelectronics Corp. 
Bus 004 Device 002: ID 03f0:1204 Hewlett-Packard DeskJet 930c
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0582:00b4 Roland Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

:~$ ```
aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

----------------------------

I installed Ubuntu Studio! Checked the forums, but no clue!

Did someone solve the problem!??? MAYDAY

---

### Post by omegvermelho on 2010-10-02
> **Hanine said:**
> I have the same problem.
My Device is an Audio Interface :

Edirol UA-25 USB.

Upon : lsusb ---->

```
$ lsusb
```Bus 005 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 0603:00f2 Novatek Microelectronics Corp. 
Bus 004 Device 002: ID 03f0:1204 Hewlett-Packard DeskJet 930c
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0582:00b4 Roland Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

:~$ ```
aplay -l
```**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

----------------------------

I installed Ubuntu Studio! Checked the forums, but no clue!

Did someone solve the problem!??? MAYDAY

Have you checked out - [http://alsa.opensrc.org/index.php/Edirol_UA-25](http://alsa.opensrc.org/index.php/Edirol_UA-25) .... 

sojournerC - more info on your system would make it easier to figure out whats going on

---

