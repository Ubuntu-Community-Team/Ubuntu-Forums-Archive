---
title: "VisionDTV DVB-S TV card - I can't get any signal"
date: 2007-08-18
forum: Multimedia &amp; Video
---

### Post by foren-sniper on 2007-08-18
Something is going complety wrong here - but I have no clue...

I put a VisionPlus VisionDTV DVB-S TV card into my machine. It has CONNEXANT chipset and should normally work out of the box. The only thing that might be required is to load the driver dvb-bt8xx.

But I'm not getting any signal from any program:
Running **GXine** I can choose DVB, but I getn error message that the data channel can not be opend.
**Kaffeine** does not show me any DVB device
and **Klear** gives a comment like 

```
Channellist loaded
zapping to 'Das Erste':
sat 0, frequency = 11837 MHz H, symbolrate 27500000, vpid = 0x0065, apid = 0x0066
AudioPid: 102
VideoPid: 101
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
opening frontend failed: No such file or directory
```

**dmesg** shows me:```

[   14.941317] bttv: Bt8xx card found (0).
[   14.941383] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 23 (level, low) -> IRQ 19
[   14.941487] bttv0: Bt878 (rev 17) at 0000:02:02.0, irq: 19, latency: 32, mmio: 0xf7efe000
[   14.941588] bttv0: detected: Twinhan VisionPlus DVB [card=113], PCI subsystem ID is 1822:0001
[   14.941651] bttv0: using: Twinhan DST + clones [card=113,autodetected]
[   14.941712] bttv0: gpio: en=00000000, out=00000000 in=00fffffe [init]
[   14.941766] bttv0: using tuner=4
[   14.978589] bttv0: add subdevice "dvb0"
[   15.152663] bt878: AUDIO driver version 0.0.0 loaded
[   15.153162] bt878: Bt878 AUDIO function found (0).
[   15.153227] ACPI: PCI Interrupt 0000:02:02.1[A] -> GSI 23 (level, low) -> IRQ 19
[   15.153326] bt878_probe: card id=[0x11822],[ Twinhan VisionPlus DVB ] has DVB functions.
[   15.153392] bt878(0): Bt878 (rev 17) at 02:02.1, irq: 19, latency: 32, memory: 0xf7eff000
```

and after

```
sudo modprobe dvb-bt8xx
```

```

[34622.392321] DVB: registering new adapter (bttv0).
[34622.710892] dst(0) dst_get_device_id: Recognise [DST-03T]
[34622.767387] dst(0) dst_check_stv0299: Found a STV0299 NIM
[34622.806216] dst(0) dst_check_mb86a15: Found a MB86A15 NIM
[34622.806223] dst(0) dst_get_device_id: [DST-03T] has a [MB 86A15]
[34622.806226] dst(0) dst_get_device_id: [DST-03T] has a [MB 86A15]
[34622.806229] DST type flags : 0x2 ts204 0x4 symdiv 0x10 firmware version = 2
[34622.842035] dst(0) dst_get_mac: MAC Address=[00:08:ca:10:bb:00]
[34622.842044] DVB: registering frontend 0 (DST DVB-S)...
```

**Klear** comments to me:

```
Loading channels list
Channelsconf is:/home/flipo/.klear//channels.conf
ControllerMain: Channels list found. Reading in....
Channellist loaded
zapping to 'Das Erste':
sat 0, frequency = 11837 MHz H, symbolrate 27500000, vpid = 0x0065, apid = 0x0066
AudioPid: 102
VideoPid: 101
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
status 00 | signal 0000 | snr 0000 | ber fffffffe | unc fffffffe | Demux: demux0
StreamReader thread started
Reading in Content
Reading sector loop
```

and **Kaffeine**:```

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
0
/dev/dvb/adapter0/frontend0 : opened ( DST DVB-S )
/dev/dvb/adapter0/frontend1 : : No such file or directory
/dev/dvb/adapter1/frontend0 : : No such file or directory
QLayout "unnamed" added to QWidget "unnamed", which already has a layout
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
kio (KLauncher): ERROR: SlavePool: No communication with slave.
```

....but nothing happens. Klear hangs - Xine does not work ..... I can't get any signal.

What is wrong? 

PLEASE help!:confused:

---

### Post by mocha on 2007-08-18
What about if you also do

sudo modprobe dst
sudo modprobe bttv

---

### Post by foren-sniper on 2007-08-19
No change ... I can't get a signal. Even the error messages are still the same.

---

### Post by mocha on 2007-08-21
Maybe there is something wrong with your options in Kaffeine.  It looks like it is looking for frontend1 in adapter0 and frontend0 in adapter1, weird..  What do you have in /dev/dvb/adapter0 ?  I have demux0, dvr0, frontend0, and net0.  Check the settings in Kaffeine to make sure it is using adapter0.  Settings - xine engine params - media - expert options - dvb.adapter, should be set to 0.

---

