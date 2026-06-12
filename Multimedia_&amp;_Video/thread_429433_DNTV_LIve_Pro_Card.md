---
title: "DNTV LIve Pro Card"
date: 2007-05-01
forum: Multimedia &amp; Video
---

### Post by Pretzal on 2007-05-01
Hi,

I have been trying for so long to get my TV tuner card to work in Ubuntu. It is a DNTV live Pro and is supposed to be supported. I feel I am so close but yet cant make it produce a TV stream. 

My dmesg gives:
[   48.133605] cx2388x cx88-mpeg Driver Manager version 0.0.6 loaded
[   48.133806] CORE cx88[0]: subsystem: 1822:0025, board: digitalnow DNTV Live! DVB-T Pro [card=42,autodetected]
[   48.133812] TV tuner 63 at 0x1fe, Radio tuner -1 at 0x1fe
[   48.166707] cx2388x v4l2 driver version 0.0.6 loaded
[   48.254370] tveeprom 0-0050: Huh, no eeprom present (err=-121)?
[   48.254516] input: cx88 IR (digitalnow DNTV Live!  as /class/input/input4
[   48.254606] cx88[0]/2: cx2388x 8802 Driver Manager
[   48.254633] PCI: Enabling device 0000:02:0e.2 (0114 -> 0116)
[   48.254653] ACPI: PCI Interrupt 0000:02:0e.2[A] -> GSI 22 (level, low) -> IRQ 23
[   48.254667] cx88[0]/2: found at 0000:02:0e.2, rev: 5, irq: 23, latency: 49, mmio: 0xe5000000
[   48.264799] PCI: Enabling device 0000:02:0e.0 (0114 -> 0116)
[   48.264813] ACPI: PCI Interrupt 0000:02:0e.0[A] -> GSI 22 (level, low) -> IRQ 23
[   48.264831] cx88[0]/0: found at 0000:02:0e.0, rev: 5, irq: 23, latency: 165, mmio: 0xe3000000
[   48.359669] tuner 0-0061: chip found @ 0xc2 (cx88[0])
[   48.362803] tuner 0-0061: type set to 63 (Philips FMD1216ME MK3 Hybrid Tuner)
[   48.365862] tuner 0-0061: type set to 63 (Philips FMD1216ME MK3 Hybrid Tuner)
[   48.380056] cx88[0]/0: registered device video0 [v4l2]
[   48.380127] cx88[0]/0: registered device vbi0
[   48.380176] cx88[0]/0: registered device radio0
[   48.466227] cx2388x dvb driver version 0.0.6 loaded
[   48.466235] cx8802_register_driver() ->registering driver type=dvb access=shared
[   48.466242] CORE cx88[0]: subsystem: 1822:0025, board: digitalnow DNTV Live! DVB-T Pro [card=42]
[   48.466350] cx88[0]/2: cx2388x based dvb card
[   48.532288] usbcore: registered new interface driver libusual
[   48.582596] cx2388x alsa driver version 0.0.6 loaded
[   48.582710] PCI: Enabling device 0000:02:0e.1 (0114 -> 0116)
[   48.582723] ACPI: PCI Interrupt 0000:02:0e.1[A] -> GSI 22 (level, low) -> IRQ 23
[   48.582770] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   48.604503] DVB: registering new adapter (cx88[0]).
[   48.604515] DVB: registering frontend 0 (Zarlink MT352 DVB-T)...


I even have a /dev/dvb/adapter0 directory with 4 files in it: demux0, dvr0, frontend0 and net0. They are all 0 bytes in size. Does this matter??

Can anyone please help me? I am desperate in trying to solve this. I believe there is a solution, only I cant find it.

---

### Post by Erlander on 2007-05-02
Try running it with Kaffeine.

Install Kaffeine from synapatic and also install libxine-extracodecs.

Rob

---

### Post by Pretzal on 2007-05-02
Oh my God....it works!!

I already had the libxine-extracodecs installed but it works with kaffeine! Thank you very much.

Now all I have to do is get it to work in Myth TV.....

---

### Post by Erlander on 2007-05-02
That's great.  I thought it would from the code you posted.

This guide works well for Mythtv.

Rob

---

