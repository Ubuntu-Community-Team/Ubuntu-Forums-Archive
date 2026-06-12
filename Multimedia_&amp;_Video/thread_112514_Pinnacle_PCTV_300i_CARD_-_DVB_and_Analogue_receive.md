---
title: "Pinnacle PCTV 300i CARD - DVB and Analogue receiver"
date: 2006-01-04
forum: Multimedia &amp; Video
---

### Post by IainUx on 2006-01-04
I have such a card, which can receive both DVB and analogue, but so far I can only get it to receive analogue...
I have successfully installed MythTv, but I can't get any DVB viewer to recognise the DVB function of that card.

Can anyone assist?

I also have a therad running on asking how I can apply a patch from LinuxTV.org, but I am not sure if this will provide the solution, which is why I am asking this question separately...

---

### Post by jamiepedder on 2006-04-16
Hi IainUx! ](*,) 

I also have the pinnacle card, and having problems doing anything with it.
I have had it running with analogue on Mandriva, but can't seem to get it to work on Ubuntu.  Keep getting some message about the tuner.

From what I've read about on the internet, we have to specify the tuner type that the card uses, but Im assuming there will be two tuners one for digital and one for analogue, unless one chip does both.

Ubuntu seems to pick it up, but doesnt recognise it as being a dvb capable card.  I've successfully modprobe'd saa7134_dvb and it loads fine, saying I have a Zarlink tuner, but still doesn't work when I use any dvb or other kind of tv software.

Does anyone have this card working in any form under Ubuntu?  And if so, can you please part with the necessary info to help us get our cards working?

Info seems to be few and far between for any distro for this card and I would really like to be able to use this card with Linux otherwise I'll have to have a dual boot again with windows.

My pc is also my bedroom telly, so its a major PITA not being able to watch tv.  Im not bothered about recording, just wanna watch TV.

Any help would be appreciated people.  Thanks.

---

### Post by schdefan on 2006-05-05
jamiepedder: Did you manage your TV card yet. I have problems with mine. When I try to scan I get the following message:
> # scan /usr/share/doc/dvb-utils/examples/scan/dvb-c/at-Vienna > /root/.tzap/channels.conf
scanning /usr/share/doc/dvb-utils/examples/scan/dvb-c/at-Vienna
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:1884: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 6 No such device or address

The device exists:

> ~# ll /dev/dvb/adapter0/
insgesamt 0
crw-rw---- 1 root video 250, 1 2006-05-05 17:13 audio0
crw-rw---- 1 root video 250, 6 2006-05-05 17:13 ca0
crw-rw---- 1 root video 250, 4 2006-05-05 17:13 demux0
crw-rw---- 1 root video 250, 5 2006-05-05 17:13 dvr0
crw-rw---- 1 root video 250, 3 2006-05-05 17:13 frontend0
crw-rw---- 1 root video 250, 7 2006-05-05 17:13 net0
crw-rw---- 1 root video 250, 8 2006-05-05 17:13 osd0
crw-rw---- 1 root video 250, 0 2006-05-05 17:13 video0



> # lspci -v | grep Pinnacle
        Subsystem: Pinnacle Systems Inc. Pinnacle PCTV Stereo (saa7134)
        Subsystem: Pinnacle Systems Inc. Studio DV

> # less /boot/config-2.6.15-21-386 | grep SAA
CONFIG_VIDEO_SAA6588=m
CONFIG_VIDEO_SAA5246A=m
CONFIG_VIDEO_SAA5249=m
CONFIG_VIDEO_SAA7134=m
CONFIG_VIDEO_SAA7134_ALSA=m
CONFIG_VIDEO_SAA7134_OSS=m
CONFIG_VIDEO_SAA7134_DVB=m
CONFIG_VIDEO_SAA7134_DVB_ALL_FRONTENDS=y
# Supported SAA7146 based PCI Adapters
CONFIG_VIDEO_SAA7146=m
CONFIG_VIDEO_SAA7146_VV=m


I am runnning a dapper installtion with a kernel 2.6.15-21-386 but I can't find the module saa7134_dvb.


Has someone an idea where can I find the module. I don't know where to start. I tried mythtv and kdetv and freevo but I think I first need configure the card.

schdefan

---

### Post by cfi on 2006-07-10
Was anbody successful?

I recently upgraded from a pure Debian system with some self-compiled kernel and modules to a stock Ubuntu Dapper Drake, and was hoping that the PCTV 300i would be working out of the box. But it doesn't. On my former debian I got the dvb part fully running (had no interest in the analogue part), but needed to path both kernel (2.6.13) and install different v4l drivers.

In Dapper at least after a
  sudo modprobe saa7134_dvb
I get all the usual dvb modules:
```

# lsmod |grep dvb
saa7134_dvb            11908  1
mt352                   6788  1 saa7134_dvb
video_buf_dvb           6660  1 saa7134_dvb
dvb_core               82984  1 video_buf_dvb
nxt200x                13444  1 saa7134_dvb
dvb_pll                11012  2 saa7134_dvb,nxt200x
tda1004x               14468  1 saa7134_dvb
saa7134               115936  2 saa7134_dvb,saa7134_alsa
video_buf              22148  4 saa7134_dvb,video_buf_dvb,saa7134_alsa,saa7134
i2c_core               21904  11 saa7134_dvb,mt352,nxt200x,tda1004x,i2c_acpi_ec,tda9887,tuner,nvidia,saa7134,ir_kbd_i2c,i2c_nforce2

```

Also the card seems to be detected correctly in /var/log/messages:
```

Jul 10 20:32:48 silvermoon kernel: [17184435.184000] saa7134[0]: pinnacle 300i dvb setup
Jul 10 20:32:48 silvermoon kernel: [17184435.192000] DVB: registering new adapter (saa7134[0]).
Jul 10 20:32:48 silvermoon kernel: [17184435.192000] DVB: registering frontend 0 (Zarlink MT352 DVB-T)...

```

Messages during booting are equally well:
```

Jul  5 21:03:49 silvermoon kernel: [17179591.576000] Linux video capture interface: v1.00
Jul  5 21:03:49 silvermoon kernel: [17179591.684000] ts: Compaq touchscreen protocol output
Jul  5 21:03:49 silvermoon kernel: [17179591.688000] saa7130/34: v4l2 driver version 0.2.14 loaded
Jul  5 21:03:49 silvermoon kernel: [17179591.688000] **** SET: Misaligned resource pointer: f7eadc02 Type 07 Len 0
Jul  5 21:03:49 silvermoon kernel: [17179591.688000] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
Jul  5 21:03:49 silvermoon kernel: [17179591.688000] ACPI: PCI Interrupt 0000:05:08.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 58Jul  5 21:03:49 silvermoon kernel: [17179591.688000] saa7134[0]: found at 0000:05:08.0, rev: 1, irq: 58, latency: 32, mmio: 0xd0000000
Jul  5 21:03:49 silvermoon kernel: [17179591.688000] saa7134[0]: subsystem: 11bd:002d, board: Pinnacle PCTV 300i DVB-T + PAL [card=50,autodetected]
Jul  5 21:03:49 silvermoon kernel: [17179591.688000] saa7134[0]: board init: gpio is c806000
Jul  5 21:03:49 silvermoon kernel: [17179591.696000] Linux agpgart interface v0.101 (c) Dave Jones
Jul  5 21:03:49 silvermoon kernel: [17179591.708000] nvidia: module license 'NVIDIA' taints kernel.
Jul  5 21:03:49 silvermoon kernel: [17179591.824000] saa7134[0]: i2c eeprom 00: bd 11 2d 00 f8 f8 1c 00 43 43 a9 1c 55 d2 b2 92
Jul  5 21:03:49 silvermoon kernel: [17179591.824000] saa7134[0]: i2c eeprom 10: 00 f0 04 04 ff 20 ff ff ff ff ff ff ff ff ff ff
Jul  5 21:03:49 silvermoon kernel: [17179591.824000] saa7134[0]: i2c eeprom 20: 01 40 01 02 03 ff 03 01 08 ff 00 25 ff ff ff ff
Jul  5 21:03:49 silvermoon kernel: [17179591.824000] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Jul  5 21:03:49 silvermoon kernel: [17179591.824000] saa7134[0]: i2c eeprom 40: ff 16 00 c0 86 3c 01 01 ff ff ff ff ff ff ff ff
Jul  5 21:03:49 silvermoon kernel: [17179591.824000] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Jul  5 21:03:49 silvermoon kernel: [17179591.824000] saa7134[0]: i2c eeprom 60: 0c 22 17 44 03 08 de 25 ff ff ff ff ff ff ff ff
Jul  5 21:03:49 silvermoon kernel: [17179591.824000] saa7134[0]: i2c eeprom 70: 00 30 8d 17 55 a6 ff ff 34 1c ff ff ff ff ff ff
Jul  5 21:03:49 silvermoon kernel: [17179591.888000] tuner 2-0060: Chip ID is not zero. It is not a TEA5767
Jul  5 21:03:49 silvermoon kernel: [17179591.888000] tuner 2-0060: chip found @ 0xc0 (saa7134[0])
Jul  5 21:03:49 silvermoon kernel: [17179591.896000] tuner 2-0060: microtune: companycode=0000 part=00 rev=00
Jul  5 21:03:49 silvermoon kernel: [17179591.896000] tuner 2-0060: microtune unknown found, not (yet?) supported, sorry :-/
Jul  5 21:03:49 silvermoon kernel: [17179591.912000] tda9887 2-0043: chip found @ 0x86 (saa7134[0])
Jul  5 21:03:49 silvermoon kernel: [17179591.920000] saa7134[0]: registered device video0 [v4l2]
Jul  5 21:03:49 silvermoon kernel: [17179591.920000] saa7134[0]: registered device vbi0
Jul  5 21:03:49 silvermoon kernel: [17179591.928000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 58Jul  5 21:03:49 silvermoon kernel: [17179591.928000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8762  Mon May 15 13:06:38 PDT 2006
Jul  5 21:03:49 silvermoon kernel: [17179591.956000] saa7134 ALSA driver for DMA sound loaded
Jul  5 21:03:49 silvermoon kernel: [17179591.956000] saa7134[0]/alsa: saa7134[0] at 0xd0000000 irq 58 registered as card -1



```



But tuning doesn't work:
```

# scan tuning.conf >test_channels.conf
scanning tuning.conf
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 198500000 1 3 0 1 1 3 0
initial transponder 490000000 0 2 0 1 1 3 0
initial transponder 498000000 0 2 0 1 1 3 0
initial transponder 506000000 0 2 0 1 1 3 0
initial transponder 530000000 0 2 0 1 1 3 0
initial transponder 594000000 0 2 0 1 1 3 0
initial transponder 658000000 0 2 0 1 1 3 0
initial transponder 786000000 0 2 0 1 1 3 0
>>> tune to: 198500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_NONE:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 198500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_NONE:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 490000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_NONE:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 490000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_NONE:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
...

```

This is a long known problem, which was already discussed on other forums and on the linuxtv mailing list. E.g.:
[http://linuxtv.org/v4lwiki/index.php/Pinnacle_PCTV_300i](http://linuxtv.org/v4lwiki/index.php/Pinnacle_PCTV_300i)
[http://gentoo-wiki.com/HARDWARE_saa7134](http://gentoo-wiki.com/HARDWARE_saa7134) (at the bottom of the page) same in German only: [http://de.gentoo-wiki.com/Pinnacle_300i](http://de.gentoo-wiki.com/Pinnacle_300i) (the part about 2.6.13.1 kernel incompatibilities was added by me in both posts)

Anybody knows an easy way out, or do we need to patch the kernel/video drivers again?

Cheers,
  cfi

---

### Post by cfi on 2006-07-10
Got it myself quite easily :-)

Here's what I did:

Based on a plain Dapper Drake installation, I updated the v4linux drivers to the most recent state. I did not have to recompile the kernel. I haven't yet tested to reboot, but will do that in a minute.

So far I did:
* Use synaptic package manager to install linux-kernel-headers of my version (-25-i386), mercury (version control system) and some other stuff which you probably don't need
* Get the latest drivers by following the instructions here: [http://www.linuxtv.org/repo/](http://www.linuxtv.org/repo/)
Commands I entered were:
```

> sudo bash
> cd /usr/src
> mkdir v4l
> cd v4l
> hg clone http://linuxtv.org/hg/v4l-dvb
> hg clone http://linuxtv.org/hg/dvb-apps
> cd v4l-dvb
> make

```
This should work fine. You can now test the modules with "make load".

Right now, my computer is at this stage. I ran Kaffeine, scanned some channels for my area (DE-Braunschweig) and am watching DVB-T TV right now :-)

Next, I'm doing a "make install" and a reboot. Will update this thread in a sec...

---

### Post by cfi on 2006-07-10
All is well.

To have dvb up and running after each reboot, I also had to add the kernel module to the /etc/modules file. My file now looks like this:
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
saa7134_dvb

```


Note again, that I cannot test analog, because in my area no analog signals are provided anymore.

Cheers,
  cfi

---

