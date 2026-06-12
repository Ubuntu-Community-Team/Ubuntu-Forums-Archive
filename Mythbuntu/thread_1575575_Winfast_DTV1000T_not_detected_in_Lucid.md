---
title: "Winfast DTV1000T not detected in Lucid"
date: 2010-09-15
forum: Mythbuntu
---

### Post by funkydan2 on 2010-09-15
Hi,

I've recently upgraded my mythbox to a desktop machine (from a laptop) so now I'm wanting to use my Winfast DTV1000T which has been sitting unused for a while.

However, the digital (DVB) part of this card isn't being detected, and so I can't add it in mythtv-setup.

I think the problem is that the cx88-dvb module isn't being loaded. I've added this module to my /etc/modules file (and also tried it with the like 'cx88-dvb card=35) but with no luck.

This is my card according to lspci:
> 
0a:09.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
	Subsystem: LeadTek Research Inc. Device 665f
	Flags: bus master, medium devsel, latency 165, IRQ 21
	Memory at d0000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: <access denied>
	Kernel driver in use: cx8800
	Kernel modules: cx8800

0a:09.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
	Subsystem: LeadTek Research Inc. Device 665f
	Flags: bus master, medium devsel, latency 49, IRQ 21
	Memory at d1000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: <access denied>
	Kernel driver in use: cx88-mpeg driver manager
	Kernel modules: cx8802


I've also tried compiling the latest v4l modules, but they fail with kernel 2.6.32 (the error thrown is to do with wanting a newer kernel).

Any tips would be greatly appreciated.

Daniel

---

### Post by d_eckert on 2010-09-16
in a terminal, run the following two commands and post the results:
[I]uname -r
lsmod[/I]

---

### Post by funkydan2 on 2010-09-16
Thanks d_eckert

uname -r
> 
2.6.32-24-generic


lsmod
> 
Module                  Size  Used by
snd_usb_audio          75765  0 
uvcvideo               56990  0 
snd_usb_lib            15801  1 snd_usb_audio
snd_hwdep               5412  1 snd_usb_audio
lirc_mceusb            12402  0 
lirc_dev                8884  1 lirc_mceusb
joydev                  8708  0 
snd_intel8x0           25588  0 
dvb_pll                 9085  0 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
cx22702                 5032  0 
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  4 snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
fbcon                  35102  71 
snd_seq_dummy           1338  0 
tileblit                2031  1 fbcon
cx88_vp3054_i2c         1808  0 
cx8800                 27188  0 
font                    7557  1 fbcon
cx8802                 12841  0 
snd_seq_oss            26726  0 
bitblit                 4707  1 fbcon
videobuf_dvb            5175  0 
tda18271               35267  1 
softcursor              1189  1 bitblit
snd_seq_midi            4557  0 
cx88xx                 72596  2 cx8800,cx8802
snd_rawmidi            19056  2 snd_usb_lib,snd_seq_midi
ir_common              38875  1 cx88xx
vga16fb                11385  0 
vgastate                8961  1 vga16fb
af9013                 19926  1 
v4l2_common            15431  2 cx8800,cx88xx
videodev               34361  4 uvcvideo,cx8800,cx88xx,v4l2_common
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
v4l1_compat            13251  2 uvcvideo,videodev
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
tveeprom               11102  1 cx88xx
btcx_risc               3624  3 cx8800,cx8802,cx88xx
snd_timer              19098  2 snd_pcm,snd_seq
dvb_usb_af9015         23159  1 
dvb_usb                14457  1 dvb_usb_af9015
lp                      7028  0 
dvb_core               86142  2 videobuf_dvb,dvb_usb
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
videobuf_dma_sg        10782  3 cx8800,cx8802,cx88xx
i915                  285586  3 
videobuf_core          16356  5 cx8800,cx8802,videobuf_dvb,cx88xx,videobuf_dma_sg
snd                    54148  12 snd_usb_audio,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         29297  1 i915
soundcore               6620  1 snd
ppdev                   5259  0 
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
parport_pc             25962  1 
intel_agp              24119  2 i915
drm                   162409  4 i915,drm_kms_helper
agpgart                31724  2 intel_agp,drm
i2c_algo_bit            5028  3 cx88_vp3054_i2c,cx88xx,i915
video                  17375  1 i915
parport                32635  3 lp,ppdev,parport_pc
output                  1871  1 video
psmouse                63245  0 
serio_raw               3978  0 
usb_storage            39425  1 
usbhid                 36110  0 
hid                    67032  1 usbhid
floppy                 53016  0 
tg3                   109324  0 


After doing some more reading yesterday, I've now added 'options cx88xx card=35' to a .conf file in /etc/modprobe.d and only have 'cx88-dvb' in my /etc/modules. (I read that with newer version of Ubuntu that's the way to apply options to kernel modules.)

---

### Post by d_eckert on 2010-09-16
do you have anything listed under /dev/dvb ?
are there any messages printed if you try to manually load the module: *modprobe cx88-dvb* ?

can you also post the output of the following:
[I]dmesg | grep cx88
dmesg | grep dvb
dmesg | grep DVB[/I]

---

### Post by funkydan2 on 2010-09-16
Thanks for your help.

The reason for the existing dvb related modules is that I also have a Winfast DTV Dongle Gold connected to the system. So some of the modules are related to that. Also, I think the WinFast DTV 1000T has both digital and analogue (it has inputs for a composite cable), and thus some cx88 modules are loaded for that.

When I try to load the module:
> 
FATAL: Error inserting cx88_dvb (/lib/modules/2.6.32-24-generic/kernel/drivers/media/video/cx88/cx88-dvb.ko): No such device

and dmesg | grep cx88
> 
[    9.973573] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.7 loaded
[    9.974748] cx88[0]: subsystem: 107d:665f, board: WinFast DTV1000-T [card=35,insmod option], frontend(s): 1
[    9.974755] cx88[0]: TV tuner type 4, Radio tuner type -1
[    9.980198] cx88/0: cx2388x v4l2 driver version 0.0.7 loaded
[   10.136229] input: cx88 IR (WinFast DTV1000-T) as /devices/pci0000:00/0000:00:1e.0/0000:0a:09.2/input/input6
[   10.136400] cx88[0]/2: cx2388x 8802 Driver Manager
[   10.136449] cx88-mpeg driver manager 0000:0a:09.2: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   10.136464] cx88[0]/2: found at 0000:0a:09.2, rev: 5, irq: 21, latency: 49, mmio: 0xd1000000
[   10.136475] IRQ 21/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   10.136971] cx8800 0000:0a:09.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   10.136985] cx88[0]/0: found at 0000:0a:09.0, rev: 5, irq: 21, latency: 165, mmio: 0xd0000000
[   10.137000] IRQ 21/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   10.137111] cx88[0]/0: registered device video0 [v4l2]
[   10.137164] cx88[0]/0: registered device vbi0
[   10.146047] cx88/2: cx2388x dvb driver version 0.0.7 loaded
[   10.146056] cx88/2: registering cx8802 driver, type: dvb access: shared
[   10.146063] cx88[0]/2: subsystem: 107d:665f, board: WinFast DTV1000-T [card=35]
[   10.146069] cx88[0]/2: cx2388x based DVB/ATSC card
[   10.146073] cx8802_alloc_frontends() allocating 1 frontend(s)
[   10.726253] cx88[0]/2: dvb_register failed (err = -22)
[   10.726302] cx88[0]/2: cx8802 probe failed, err = -22
[   10.778270] cx88/2: cx2388x dvb driver version 0.0.7 loaded
[   10.778278] cx88/2: registering cx8802 driver, type: dvb access: shared
[   10.778284] cx88[0]/2: subsystem: 107d:665f, board: WinFast DTV1000-T [card=35]
[   10.778290] cx88[0]/2: cx2388x based DVB/ATSC card
[   10.778294] cx8802_alloc_frontends() allocating 1 frontend(s)
[   10.781607] cx88[0]/2: dvb_register failed (err = -22)
[   10.781682] cx88[0]/2: cx8802 probe failed, err = -22


dmesg | grep - i dvb
> 
[    8.996348] dvb-usb: found a 'Leadtek WinFast DTV Dongle Gold' in warm state.
[    8.997521] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[    8.997921] DVB: registering new adapter (Leadtek WinFast DTV Dongle Gold)
[    9.314606] DVB: registering adapter 0 frontend 0 (Afatech AF9013 DVB-T)...
[   10.146047] cx88/2: cx2388x dvb driver version 0.0.7 loaded
[   10.146056] cx88/2: registering cx8802 driver, type: dvb access: shared
[   10.146069] cx88[0]/2: cx2388x based DVB/ATSC card
[   10.211852] dvb-usb: Leadtek WinFast DTV Dongle Gold successfully initialized and connected.
[   10.222077] usbcore: registered new interface driver dvb_usb_af9015
[   10.726253] cx88[0]/2: dvb_register failed (err = -22)
[   10.778270] cx88/2: cx2388x dvb driver version 0.0.7 loaded
[   10.778278] cx88/2: registering cx8802 driver, type: dvb access: shared
[   10.778290] cx88[0]/2: cx2388x based DVB/ATSC card
[   10.781607] cx88[0]/2: dvb_register failed (err = -22)


Thanks for your help!

---

### Post by d_eckert on 2010-09-16
Can you try without the Winfast DTV Dongle Gold connected to see if maybe there is some sort of resource conflict between the two devices.

also, maybe try booting into an older kernel in case there is a bug in the driver in 2.6.32-24. You'll probably need to hold the Shift key when booting to get the GRUB menu to show to select a different kernel.

---

### Post by funkydan2 on 2010-09-17
Thanks for those ideas, I will try booting without the dongle, but I think I've tried that before without much luck.

Regarding an older kernel, the only one available in synaptic which is significantly older is 2.6.31-*-rt. I've not tried a realtime kernel before, are they less stable?

BTW - do you have this device working with lucid?

Thanks for those suggestions.

---

### Post by d_eckert on 2010-09-17
Found this for a different card, but it might work for you as well, just change the card=51 to the correct number for your card.
It may be that an incorrect module is being loaded and that is preventing cx88-dvb from loading.

[I]#!/bin/bash

rmmod cx8800
rmmod cx88-alsa
rmmod cx8802
rmmod cx88xx
modprobe cx88xx card=51
modprobe cx88-dvb


fwiw, cx8802 reloads, but the others do not. I placed this in my /etc/conf.d/local.start folder and so cx88-dvb loads on boot! [/I]

---

### Post by funkydan2 on 2010-09-18
That last idea sounds interesting, but I'm not sure how to apply it in Ubuntu since it doesn't have and /etc/conf.d/local.start setup?

I found the forum you may have got that idea from, and tried blacklisting some of the modules that it implied were problematic, but no luck - yet!

Still hoping that I may find someone who has successfully got this working.

---

### Post by funkydan2 on 2010-09-18
Hmm, I wonder if this means much!

In my first post, the output of lspci gives the identifier of my card as either 0a:09.0 or 0a:09.2, but in [CARDLIST.cxx](http://linuxtv.org/hg/v4l-dvb?cmd=file;file=linux/Documentation/video4linux/CARDLIST.cx88;filenode=-1;style=raw) the Winfast DTV 1000t is listed as 107d:665f. Could that be the source of my pain?

---

### Post by d_eckert on 2010-09-18
does it work if you run the rmmmod and modprobe lines from my previous post manually in a terminal?

---

### Post by funkydan2 on 2010-09-19
This is interesting - seems that there's a problem with cxx-alsa (see below)! Maybe that's the root of the problem? (Over the weekend I compiled the latest v4l modules from mercurial, but no improvement.)

> 
saunders@MythBox:~$ sudo rmmod cx8800
[sudo] password for saunders: 
saunders@MythBox:~$ sudo rmmod cx88-alsa
ERROR: Module cx88_alsa does not exist in /proc/modules
saunders@MythBox:~$ sudo rmmod cx8802
saunders@MythBox:~$ sudo rmmod cx88xx
saunders@MythBox:~$ sudo modprobe cx88xx card=35
saunders@MythBox:~$ sudo modprobe cx88-dvb
FATAL: Error inserting cx88_dvb (/lib/modules/2.6.32-24-generic/kernel/drivers/media/video/cx88/cx88-dvb.ko): No such device


---

### Post by d_eckert on 2010-09-20
I've been doing a bit of searching on the net and found a few references to a cx88-blackbird module. can you try loading it instead of cx88-dvb?

---

### Post by funkydan2 on 2010-09-20
nah, similar types of errors...

> 
FATAL: Error inserting cx88_blackbird (/lib/modules/2.6.32-24-generic/kernel/drivers/media/video/cx88/cx88-blackbird.ko): No such device


I'm surprised that there aren't others out there with either the same problem, or a solution, since this card used to be quite popular for MythTV boxes. Maybe they haven't upgraded to Lucid?

---

### Post by Ram-Z on 2010-12-31
Hi, I seem to have the same problem with a Hauppauge HVR4000 card. Any help would be appreciated.

uname -rm
> 2.6.32-27-server x86_64lsb_release -a
> 
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04.1 LTS
Release:    10.04
Codename:    lucid> ramsi@tardis:~/src/v4l-dvb$ sudo modprobe cx88xx card=68
ramsi@tardis:~/src/v4l-dvb$ sudo modprobe cx88-dvb 
FATAL: Error inserting cx88_dvb (/lib/modules/2.6.32-27-server/kernel/drivers/media/video/cx88/cx88-dvb.ko): No such device
ramsi@tardis:~/src/v4l-dvb$ sudo modprobe cx88-blackbird 
FATAL: Error inserting cx88_blackbird (/lib/modules/2.6.32-27-server/kernel/drivers/media/video/cx88/cx88-blackbird.ko): No such device
dmesg | grep -C 10 cx
> [ 2522.509599] IR NEC protocol handler initialized
[ 2522.521957] Linux video capture interface: v2.00
[ 2522.521961] WARNING: You're using an experimental version of the V4L stack. As the driver
[ 2522.521963]          is backported to an older kernel, it doesn't offer enough quality for
[ 2522.521965]          its usage in production.
[ 2522.521966]          Use it with care.
[ 2522.524819] IR RC5(x) protocol handler initialized
[ 2522.529448] IR RC6 protocol handler initialized
[ 2522.531395] IR JVC protocol handler initialized
[ 2522.532841] IR Sony protocol handler initialized
[ 2529.721818] WARNING: You're using an experimental version of the DVB stack. As the driver
[ 2529.721823]          is backported to an older kernel, it doesn't offer enough quality for
[ 2529.721826]          its usage in production.
[ 2529.721829]          Use it with care.
[ 2529.733960] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.8 loaded
[ 2529.734662] cx88[0]: subsystem: 0070:6902, board: Hauppauge WinTV-HVR4000 DVB-S/S2/T/Hybrid [card=68,insmod option], frontend(s): 2
[ 2529.734670] cx88[0]: TV tuner type 63, Radio tuner type -1
[ 2529.862212] cx88[0]: i2c init: enabling analog demod on HVR1300/3000/4000 tuner
[ 2529.881297] tuner 2-0043: chip found @ 0x86 (cx88[0])
[ 2529.886116] tda9887 2-0043: creating new instance
[ 2529.886119] tda9887 2-0043: tda988[5/6/7] found
[ 2529.890805] tuner 2-0061: chip found @ 0xc2 (cx88[0])
[ 2529.935664] tveeprom 2-0050: Hauppauge model 69009, rev B5D3, serial# 7151981
[ 2529.935666] tveeprom 2-0050: MAC address is 00:0d:fe:6d:21:6d
[ 2529.935668] tveeprom 2-0050: tuner model is Philips FMD1216MEX (idx 133, type 78)
[ 2529.935671] tveeprom 2-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xf4)
[ 2529.935673] tveeprom 2-0050: audio processor is CX880 (idx 30)
[ 2529.935675] tveeprom 2-0050: decoder processor is CX880 (idx 20)
[ 2529.935676] tveeprom 2-0050: has radio, has IR receiver, has no IR transmitter
[ 2529.935678] cx88[0]: hauppauge eeprom: model=69009
[ 2529.941574] tuner-simple 2-0061: creating new instance
[ 2529.941578] tuner-simple 2-0061: type set to 78 (Philips FMD1216MEX MK3 Hybrid Tuner)
[ 2529.970093] Registered IR keymap rc-hauppauge-new
[ 2529.970280] input: cx88 IR (Hauppauge WinTV-HVR400 as /devices/pci0000:00/0000:00:14.4/0000:03:07.2/rc/rc0/input9
[ 2529.970381] rc0: cx88 IR (Hauppauge WinTV-HVR400 as /devices/pci0000:00/0000:00:14.4/0000:03:07.2/rc/rc0
[ 2529.970389] cx88[0]/2: cx2388x 8802 Driver Manager
[ 2529.970414] cx88-mpeg driver manager 0000:03:07.2: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[ 2529.970432] cx88[0]/2: found at 0000:03:07.2, rev: 5, irq: 21, latency: 32, mmio: 0xfb000000
[ 2529.970445] IRQ 21/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[ 2529.976315] cx88/2: cx2388x dvb driver version 0.0.8 loaded
[ 2529.976321] cx88/2: registering cx8802 driver, type: dvb access: shared
[ 2529.976328] cx88[0]/2: subsystem: 0070:6902, board: Hauppauge WinTV-HVR4000 DVB-S/S2/T/Hybrid [card=68]
[ 2529.976334] cx88[0]/2: cx2388x based DVB/ATSC card
[ 2529.976338] cx8802_alloc_frontends() allocating 2 frontend(s)
[ 2529.992205] cx88[0]/2: dvb_register failed (err = -22)
[ 2529.992209] cx88[0]/2: cx8802 probe failed, err = -22
[ 2530.083375] cx88/2: cx2388x dvb driver version 0.0.8 loaded
[ 2530.083382] cx88/2: registering cx8802 driver, type: dvb access: shared
[ 2530.083391] cx88[0]/2: subsystem: 0070:6902, board: Hauppauge WinTV-HVR4000 DVB-S/S2/T/Hybrid [card=68]
[ 2530.083398] cx88[0]/2: cx2388x based DVB/ATSC card
[ 2530.083402] cx8802_alloc_frontends() allocating 2 frontend(s)
[ 2530.086432] cx88[0]/2: dvb_register failed (err = -22)
[ 2530.086438] cx88[0]/2: cx8802 probe failed, err = -22


---

