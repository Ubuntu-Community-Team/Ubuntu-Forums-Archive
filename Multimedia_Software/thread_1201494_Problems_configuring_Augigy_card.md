---
title: "Problems configuring Augigy card"
date: 2009-07-01
forum: Multimedia Software
---

### Post by lunarul on 2009-07-01
Hello, I have a Soundblaster Audigy card (not very sure about further details, it's an old card) and I can't get it to work properly on Ubuntu (currently 9.04, but the problem was there before upgrading from 8.10)
I can hear OS sounds (startup and shutdown), browser sounds, play music in Audacious and movies in VLC. But only front and center speakers work.
If I open Totem, I hear sound only from rear speakers and subwoofer.
If I open a 5.1 sound in VLC and select 5.1 in the device menu, VLC crashes.
Using speaker-test, I can only hear the front and center speakers. Rear left and rear right sounds can be heard faintly from the corresponding front speakers.

I tried searching everywhere, found all kinds of guides, but nothing worked and most info was old.

Output of  `aplay -l`:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```My card should be the CA0106 one.

Output of `lspci` :
```
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 5
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller
01:00.0 VGA compatible controller: ATI Technologies Inc RV670PRO [Radeon HD 3850]
01:00.1 Audio device: ATI Technologies Inc Radeon HD 3870 Audio device
02:00.0 Ethernet controller: Attansic Technology Corp. L1e Gigabit Ethernet Adapter (rev b0)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II Controller (rev b2)
05:00.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
05:01.0 Communication controller: Intel Corporation 536EP Data Fax Modem
05:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)

```I have no `.asoundrc` file in my home directory.

Can anyone please help me get this to work properly? I want to solve the Totem problem and make surround sound work.

---

### Post by lunarul on 2009-07-02
anybody?

---

### Post by SR_ELPIRATA on 2009-07-14
By the way you referred to your card "CA0106", we may have the same card, however, I havent moved to 9.04, I'm still in 8.10.

In my case, in the System>Preferences>Sound under Sounds I selected the Audigy SE (SB0570) CA0106 in ALSA and I can hear the test sound from any of the 5.1 plugs I'm currently using.

I noted on some threads that is recommended to disable the onboard audio and I'm yet to test this. So far I get mixed results.

In Rhythmbox I get sound only from Center/Sub.
In Firefox at the moment nothing at all.

I'll test other apps as I go thru with it. I recommend reading the Comprehensive Audio guide: [http://ubuntuforums.org/showthread.php?t=205449&highlight=Audigy](http://ubuntuforums.org/showthread.php?t=205449&highlight=Audigy) which may help you understand whats going on. Out of the top of my head Id think your problem is related to the PulseAudio thingie. I can't say for sure, but I sort of remember reading somewhere that the Creative cards didnt support it much, that Alsa could work though, so maybe all you need is to go back to alsa.

I'll reply with more data as I go along, but dont expect too much since I'm also a noob :P

ELP

---

