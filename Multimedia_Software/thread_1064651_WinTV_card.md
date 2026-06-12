---
title: "WinTV card"
date: 2009-02-09
forum: Multimedia Software
---

### Post by dsmith1974 on 2009-02-09
After installing a Hauppuage WinTV NOVA HD DVB-S I get the following from dmesg after booting:

<code>
dusmith@dcfap1:~$ dmesg |grep cx
[ 11.662728] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.6 loaded
[ 11.663232] cx88[0]: subsystem: 0070:6906, board: Hauppauge WinTV-HVR4000(Lite) DVB-S/S2 [card=69,autodetected], frontend(s): 1
[ 11.663234] cx88[0]: TV tuner type -1, Radio tuner type -1
[ 11.673694] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[ 11.775436] cx2388x alsa driver version 0.0.6 loaded
[ 12.069961] cx88[0]: hauppauge eeprom: model=69100
[ 12.070018] input: cx88 IR (Hauppauge WinTV-HVR400 as /devices/pci0000:00/0000:00:1e.0/0000:05:01.2/input/input6
[ 12.105600] cx88[0]/2: cx2388x 8802 Driver Manager
[ 12.105614] cx88-mpeg driver manager 0000:05:01.2: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 12.105624] cx88[0]/2: found at 0000:05:01.2, rev: 5, irq: 17, latency: 64, mmio: 0xfc000000
[ 12.105772] cx8800 0000:05:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 12.105792] cx88[0]/0: found at 0000:05:01.0, rev: 5, irq: 17, latency: 64, mmio: 0xfa000000
[ 12.105934] cx88[0]/0: registered device video0 [v4l2]
[ 12.105966] cx88[0]/0: registered device vbi0
[ 12.146406] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[ 12.146409] cx88/2: registering cx8802 driver, type: dvb access: shared
[ 12.146412] cx88[0]/2: subsystem: 0070:6906, board: Hauppauge WinTV-HVR4000(Lite) DVB-S/S2 [card=69]
[ 12.146414] cx88[0]/2: cx2388x based DVB/ATSC card
[ 12.146416] cx8802_alloc_frontends() allocating 1 frontend(s)
[ 12.173681] cx88_audio 0000:05:01.1: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 12.173706] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[ 12.193985] cx88[0]/2: dvb_register failed (err = -22)
[ 12.193990] cx88[0]/2: cx8802 probe failed, err = -22
</code>

What's wrong?

Many thanks,

Duncan

---

