---
title: "Using optical out, cannot get passthrough audio working"
date: 2012-12-23
forum: Multimedia Software
---

### Post by oddworld on 2012-12-23
Hello, and thank you for your help!

My setup uses 5.1 speakers over toslink optical (Logitech Z-5500). I am trying to get **passthrough audio** to send DTS directly to the receiver. IEC958 is not listed in alsamixer, please help me troubleshoot getting it loaded properly. 

My computer runs Asus P5B deluxe with the Intel onboard audio. The motherboard has three sets of audio outputs: optical, coax, and the 5.1 channel analog 1/8" jacks. The system is debian wheezy (command line only...no desktop environment). Given the similar nature to ubuntu, I thought I would ask here.

My understanding is that if I can get IEC958 listed in alsamixer, I should be able to output DTS in passthrough audio. The problem is that IEC958 is not listed in alsamixer. 

```

root@xmbc-streamer:/home/oddworld# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
root@xmbc-streamer:/home/oddworld#

```

```

root@xmbc-streamer:/home/oddworld# aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=Intel
    HDA Intel, AD198x Analog
    Default Audio Device
sysdefault:CARD=Intel
    HDA Intel, AD198x Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
[B]iec958:CARD=Intel,DEV=0
    HDA Intel, AD198x Digital
    IEC958 (S/PDIF) Digital Audio Output[/B]
root@xmbc-streamer:/home/oddworld#

```

```
root@xmbc-streamer:/home/oddworld# lspci
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HR/HO/HH (ICH8R/DO/DH) 6 port SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: NVIDIA Corporation G71 [GeForce 7950 GT] (rev a1)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
03:00.0 SATA controller: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 02)
03:00.1 IDE interface: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 02)
05:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx]
05:04.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
root@xmbc-streamer:/home/oddworld#

```

```

root@xmbc-streamer:/home/oddworld# lsmod | grep snd*
snd_hda_codec_analog    78059  1
snd_hda_intel          26345  2
snd_hda_codec          78031  2 snd_hda_intel,snd_hda_codec_analog
snd_hwdep              13186  1 snd_hda_codec
snd_pcm                63900  3 snd_hda_codec,snd_hda_intel
snd_page_alloc         13003  2 snd_pcm,snd_hda_intel
snd_seq                45093  0
snd_seq_device         13176  1 snd_seq
snd_timer              22917  2 snd_seq,snd_pcm
snd                    52850  11 snd_timer,snd_seq_device,snd_seq,snd_pcm,snd_hwdep,snd_hda_codec,snd_hda_intel,snd_hda_codec_analog
soundcore              13065  1 snd
root@xmbc-streamer:/home/oddworld#

```

---

### Post by oddworld on 2012-12-24
I fixed it. I'm not sure which package did it, but future readers should isntall:

```
 alsa-tools, alsa-oss, libmad0, libmad0-dev, libmadlib, alsa-utils 
```

---

