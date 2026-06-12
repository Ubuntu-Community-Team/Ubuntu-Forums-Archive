---
title: "Hauppauge HVR4000"
date: 2013-03-26
forum: Mythbuntu
---

### Post by ITHomes on 2013-03-26
I thought I would post this here regarding my HVR4000, on ubuntu 10.04. I was getting /dev/dvb with adapter0 loaded and multiple frontends. I now have 12.04 and no /dev/dvb.


here is lspci -v

Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
        Subsystem: Hauppauge computer works Inc. WinTV HVR-4000-HD
        Flags: bus master, medium devsel, latency 165, IRQ 48
        Memory at f9000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: <access denied>
        Kernel driver in use: cx8800
        Kernel modules: cx8800


03:01.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
        Subsystem: Hauppauge computer works Inc. WinTV HVR-4000-HD
        Flags: bus master, medium devsel, latency 33, IRQ 48
        Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: <access denied>
        Kernel driver in use: cx88_audio
        Kernel modules: cx88-alsa


03:01.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
        Subsystem: Hauppauge computer works Inc. WinTV HVR-4000-HD
        Flags: bus master, medium devsel, latency 49, IRQ 48
        Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: <access denied>
        Kernel driver in use: cx88-mpeg driver manager
        Kernel modules: cx8802


03:01.4 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)
        Subsystem: Hauppauge computer works Inc. WinTV HVR-4000-HD
        Flags: bus master, medium devsel, latency 49, IRQ 10
        Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: <access denied>

my dmesg info



cx88/2: cx2388x dvb driver version 0.0.9 loaded
[   18.867458] cx88/2: registering cx8802 driver, type: dvb access: shared
[   18.867468] cx88[0]/2: subsystem: 0070:6902, board: Hauppauge WinTV-HVR4000 DVB-S/S2/T/Hybrid [card=68]
[   18.879851] cx88[0]/0: registered device video0 [v4l2]
[   18.880180] cx88[0]/0: registered device vbi0
[   18.880425] cx88[0]/0: registered device radio0
[   18.882490] cx88_audio 0000:03:01.1: PCI INT A -> GSI 48 (level, low) -> IRQ 48
[   18.882574] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   18.884546] cx88[0]/2: cx2388x based DVB/ATSC card
[   18.884557] cx8802_alloc_frontends() allocating 2 frontend(s)
[   18.948331] tuner-simple 0-0061: attaching existing instance
[   18.948341] tuner-simple 0-0061: couldn't set type to 63. Using 78 (Philips FMD1216MEX MK3 Hybrid Tuner) instead
[   18.956149] DVB: registering new adapter (cx88[0])
[   18.956176] cx88-mpeg driver manager 0000:03:01.2: DVB: registering adapter 0 frontend 0 (Conexant CX24116/CX24118)...
[   18.957271] cx88-mpeg driver manager 0000:03:01.2: DVB: registering adapter 0 frontend 1 (Conexant CX22702 DVB-T)...


and lastly dmesg | grep dvb

[   18.867447] cx88/2: cx2388x dvb driver version 0.0.9 loaded
[   18.867458] cx88/2: registering cx8802 driver, type: dvb access: shared
[42724.152269] cx24116_firmware_ondemand: Waiting for firmware upload (dvb-fe-cx24116.fw)...

I installed the last V4l drivers

Thanks for reading and for any help

---

