---
title: "Weird timeout errors"
date: 2008-11-21
forum: Multimedia Software
---

### Post by Bloemetjesgordijn on 2008-11-21
Hi guys

As a Linux newbie I have been tinkering for weeks to get my TV card working. I am getting there one step at a time, but I really need your help now.

I have two issues left
**1- Cannot select Analogue**

HVR3000 is a tri card, meaning that it has DVB-T, DVB-C and analogue
At home I only have Analogue / cable but no channels can be found (I cant select Analogue in Kaffeine)
What can I do to get Analogue channels????

**2- Weird timeout errors**

Scanning in command promt: "scan -c" gives weird errors

```
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
dumping lists (0 services)
```


Pretty please with sugar on top, please help me here. As I am completely lost now.



Cheerz 
Bloemetjesgordijn

More details
This is the dump I receive when "dmesg | grep cx"
```
[   12.495739] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   12.525910] cx2388x alsa driver version 0.0.6 loaded
[   12.597937] cx8800 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   12.598960] cx88[0]: subsystem: 0070:1402, board: Hauppauge WinTV-HVR3000 TriMode Analog/DVB-S/DVB-T [card=53,autodetected], frontend(s): 2
[   12.598963] cx88[0]: TV tuner type 63, Radio tuner type -1
[   12.718618] cx88[0]: i2c init: enabling analog demod on HVR1300/3000/4000 tuner
[   12.805406] tuner' 1-0043: chip found @ 0x86 (cx88[0])
[   12.828541] tuner' 1-0061: chip found @ 0xc2 (cx88[0])
[   12.829798] tuner' 1-0063: chip found @ 0xc6 (cx88[0])
[   12.885344] cx88[0]: hauppauge eeprom: model=14109
[   12.917277] input: cx88 IR (Hauppauge WinTV-HVR300 as /devices/pci0000:00/0000:00:14.4/0000:03:07.0/input/input6
[   12.973224] cx88[0]/0: found at 0000:03:07.0, rev: 5, irq: 21, latency: 32, mmio: 0xf9000000
[   12.989523] wm8775' 1-001b: chip found @ 0x36 (cx88[0])
[   12.997948] cx88[0]/0: registered device video0 [v4l2]
[   12.997979] cx88[0]/0: registered device vbi0
[   12.998007] cx88[0]/0: registered device radio0
[   13.003458] cx88_audio 0000:03:07.1: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   13.003481] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   14.329001] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.6 loaded
[   14.329036] cx88[0]/2: cx2388x 8802 Driver Manager
[   14.329050] cx88-mpeg driver manager 0000:03:07.2: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   14.329060] cx88[0]/2: found at 0000:03:07.2, rev: 5, irq: 21, latency: 32, mmio: 0xfb000000
[   14.329068] cx8802_probe() allocating 2 frontend(s)
[   14.347369] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[   14.347373] cx88/2: registering cx8802 driver, type: dvb access: shared
[   14.347376] cx88[0]/2: subsystem: 0070:1402, board: Hauppauge WinTV-HVR3000 TriMode Analog/DVB-S/DVB-T [card=53]
[   14.347380] cx88[0]/2: cx2388x based DVB/ATSC card
[   14.410603] DVB: registering new adapter (cx88[0])
```

---

