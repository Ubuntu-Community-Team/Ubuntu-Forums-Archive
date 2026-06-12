---
title: "TV Tuner does not find channels"
date: 2009-04-26
forum: Multimedia Software
---

### Post by thespringlion on 2009-04-26
I'm trying play TV with a Conexant CX23885 card.

So far it seems as if the kernel module and driver is loaded correctly - from lspci:

```
03:00.0 Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 02)
        Subsystem: Hauppauge computer works Inc. Device 71d1
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at fe600000 (64-bit, non-prefetchable) [size=2M]
        Capabilities: [40] Express Endpoint, MSI 00
        Capabilities: [80] Power Management version 2
        Capabilities: [90] Vital Product Data <?>
        Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [100] Advanced Error Reporting <?>
        Capabilities: [200] Virtual Channel <?>
        Kernel driver in use: cx23885
        Kernel modules: cx23885
```dmesg also reports that the firmware loads ok:

```
[   80.885327] tda10048_firmware_upload: waiting for firmware upload (dvb-fe-tda10048-1.0.fw)...
[   80.885332] i2c-adapter i2c-0: firmware: requesting dvb-fe-tda10048-1.0.fw
[   80.913858] tda10048_firmware_upload: firmware read 24878 bytes.
[   80.913861] tda10048_firmware_upload: firmware uploading
[   83.500476] tda10048_firmware_upload: firmware uploaded

```However, when I try to scan for channels, each frequency fails:

```
#scan -vv /usr/share/dvb/dvb-t/au-Melbourne
scanning /usr/share/dvb/dvb-t/au-Melbourne
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 226500000 1 3 9 3 1 1 0
initial transponder 177500000 1 3 9 3 1 1 0
initial transponder 191625000 1 3 9 3 1 1 0
initial transponder 219500000 1 3 9 3 1 1 0
initial transponder 536625000 1 2 9 3 1 2 0
>>> tune to: 226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
WARNING: >>> tuning failed!!!
#AND SO ON

```Someone suggested that the signal might be too weak so I checked the antenna and hardware in my Vista Partition.  But in Windows everything is in good working order. 

I'm not quite sure where to go from here.  I know the hardware works.  The driver loads without errors and the firmware is installed.  How do I troubleshoot from here?

---

