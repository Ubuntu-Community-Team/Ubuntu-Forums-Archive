---
title: "soundcard recognized and working, but yet no sound"
date: 2008-04-21
forum: Multimedia &amp; Video
---

### Post by gianluca.colucci on 2008-04-21
Hello everybody,

After a long time that I did not play with Linux, I have recently installed Ubuntu 8.04.
Things are changed a lot, much easier to configure a "desktop" system, but... I am facing problems in getting my on-board soundcard to work. I tried to follow the advices and suggestions in other similar threads, but it still does not work.

First of all, I wanna assure you all that the "hardware" settings are fine, I double checked the pin settings on the board, and also the sound was working in the previous system, installed on the same hardware configuration.

Some additional info:

aplay -l returns:

**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci returns:

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
02:02.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
02:02.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
02:02.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65)
02:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 01)


Moreover, I tried to update the drivers but without any success. I have tried to remove and reinstall everything related to ALSA, but nothing changed. And also, I checked whether or not there was something muted, but everything should be alright.

Is there anyone that faced a similar problem and/or knows how to help me?

Thanks a lot,

Regards,
Gianluca

---

### Post by Zorael on 2008-04-21
I can confirm this on my Acer Aspire 9815 and its Intel HDA circuit, as well. It worked great in Feisty and Gutsy, and now it regressed and won't make any sounds at all. It shows up properly, I can change volumes and everything, but there's no sound output.

```
zorael@sunspire:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

zorael@sunspire:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
**00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)**
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GHM (ICH7-M DH) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 12)
07:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
09:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
09:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
09:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
09:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

zorael@sunspire:~$ lshw -C multimedia
WARNING: you should run this program as super-user.
  *-multimedia
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

zorael@sunspire:~$ lsmod | grep snd
**snd_hda_intel         440408  1**
snd_pcm_oss            47648  0
snd_mixer_oss          20224  1 snd_pcm_oss
[b]snd_pcm                92168  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         13200  2 snd_hda_intel,snd_pcm
snd_hwdep              12552  1 snd_hda_intel[/b]
snd_seq_dummy           5764  0
snd_seq_oss            38912  0
snd_seq_midi           10688  0
snd_rawmidi            29856  1 snd_seq_midi
snd_seq_midi_event     10112  2 snd_seq_oss,snd_seq_midi
snd_seq                63232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27912  2 snd_pcm,snd_seq
snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
**snd                    70856  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device**
soundcore              10400  1 snd
```

---

### Post by gianluca.colucci on 2008-04-21
Is there anyone who managed to sort this out?

---

### Post by gianluca.colucci on 2008-04-27
Hello everybody again,

I am really in trouble with this soundcard.
I have tried to recompile the ALSA drivers but that did not solved the problem.

I really do not understand why it does not work. There are just few other people with the same issue, but what I wanna say is that does not seem to be a common problem to all ICH5-based soundcards' owners.

Is there anybody that could advice me on how to sort this out?

Thanks in advance,
Gianluca.

---

### Post by Zorael on 2008-04-27
[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/211644](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/211644)

Hopefully it'll get developer attention soon.

---

### Post by gianluca.colucci on 2008-04-27
If it can be any useful, I am trying in this exact instant a Gutsy (7.10) and I have exactly the same problem that I face in the 8.04: hardware recognized,  modules loaded, I try to play a WAV with the standard players and I don't get any error and any sound either!

So, it seems like if it is a problem with this specific hardware, not just in the newest release of Ubuntu, but also in the previous ones.

Thanks,
Gianluca.

PS: Where should I report the problem? Is there any official way to ask for a  resolution?

Thanks again.

---

### Post by NoobieDoobieDo on 2008-07-03
I can confirm that *my* no sound problem was caused by an UPDATE of the linux-image/header packages.

When I installed from my 8.04 cd sound was PERFECT - now that I've ran this update I have no sound.

Fantastic work.

---

