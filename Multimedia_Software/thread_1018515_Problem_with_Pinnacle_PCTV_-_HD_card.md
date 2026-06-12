---
title: "Problem with Pinnacle PCTV - HD card"
date: 2008-12-22
forum: Multimedia Software
---

### Post by wayneschutz on 2008-12-22
My primary goal is to convert my home VCR tapes into DVDs with a secondary goal of watching TV
on my linux server (via mythtv).  So....
I bought a Pinnacle PCTV HD PCI video capture card and installed it on my Ubuntu server (latest updates):

"Linux firewall 2.6.24-22-server #1 SMP Mon Nov 24 19:14:19 UTC 2008 i686 GNU/Linux"

An lspci gives:

...
02:0a.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
02:0a.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
02:0a.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
...

Since the card wasn't recognized by the cx88xx driver, I updated the driver according to the
instructions here:

[http://www.mythtv.org/wiki/index.php/Pinnacle_PCTV_HD_Card_(800i](http://www.mythtv.org/wiki/index.php/Pinnacle_PCTV_HD_Card_(800i))

PRIOR to updating the driver, I saw a /dev/video0 and /dev/vbi0 devices, and was able to use tvtime to
watch composite input from my VCR machine.  (But there was no /dev/dvb device.)  Now, I have a
/dev/dvb device:

wayne@firewall:~$ ll /dev/dvb
total 0
drwxr-xr-x 2 root root 120 2008-12-21 18:50 adapter0
wayne@firewall:~$ ll /dev/dvb/adapter0/
total 0
crw-rw----+ 1 root video 212, 1 2008-12-21 18:50 demux0
crw-rw----+ 1 root video 212, 2 2008-12-21 18:50 dvr0
crw-rw----+ 1 root video 212, 0 2008-12-21 18:50 frontend0
crw-rw----+ 1 root video 212, 3 2008-12-21 18:50 net0

But, no /dev/video0 nor /dev/vbi0 device.

The relevent section of the log shows ....

```
Dec 21 18:51:05 firewall kernel: [   48.194468] Linux video capture interface: v2.00
Dec 21 18:51:05 firewall kernel: [   48.678652] parport_pc 00:0c: reported by Plug and Play ACPI
Dec 21 18:51:05 firewall kernel: [   48.678765] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
Dec 21 18:51:05 firewall kernel: [   48.862322] eth0: DSPCFG accepted after 0 usec.
Dec 21 18:51:05 firewall kernel: [   48.862334] eth0: link up.
Dec 21 18:51:05 firewall kernel: [   48.862357] eth0: Setting full-duplex based on negotiated link capability.
Dec 21 18:51:05 firewall kernel: [   49.193304] cx8800: disagrees about version of symbol v4l_compat_ioctl32
Dec 21 18:51:05 firewall kernel: [   49.193313] cx8800: Unknown symbol v4l_compat_ioctl32
Dec 21 18:51:05 firewall kernel: [   49.347826] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.6 loaded
Dec 21 18:51:05 firewall kernel: [   49.348136] cx88[0]: subsystem: 11bd:0051, board: Pinnacle PCTV HD 800i [card=58,autodetected], frontend(s): 1
Dec 21 18:51:05 firewall kernel: [   49.348143] cx88[0]: TV tuner type 76, Radio tuner type -1
Dec 21 18:51:05 firewall kernel: [   49.918133] tuner' 0-0064: chip found @ 0xc8 (cx88[0])
Dec 21 18:51:05 firewall kernel: [   50.402466] xc5000 0-0064: creating new instance
Dec 21 18:51:05 firewall kernel: [   50.403463] xc5000: Successfully identified at address 0x64
Dec 21 18:51:05 firewall kernel: [   50.403467] xc5000: Firmware has not been loaded previously
Dec 21 18:51:05 firewall kernel: [   50.404458] xc5000: waiting for firmware upload (dvb-fe-xc5000-1.1.fw)...
Dec 21 18:51:05 firewall kernel: [   50.985224] NET: Registered protocol family 10
Dec 21 18:51:05 firewall kernel: [   50.985741] lo: Disabled Privacy Extensions
Dec 21 18:51:05 firewall kernel: [   53.399542] xc5000: firmware read 12332 bytes.
Dec 21 18:51:05 firewall kernel: [   53.399549] xc5000: firmware upload
Dec 21 18:51:05 firewall kernel: [   53.399555] cx88[0]: Calling XC5000 callback
Dec 21 18:51:05 firewall kernel: [   56.670403] input: cx88 IR (Pinnacle PCTV HD 800i) as /devices/pci0000:00/0000:00:1e.0/0000:02:0a.2/input/input7
Dec 21 18:51:05 firewall kernel: [   56.730253] cx88[0]/2: cx2388x 8802 Driver Manager
Dec 21 18:51:05 firewall kernel: [   56.730553] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 10
Dec 21 18:51:05 firewall kernel: [   56.730561] ACPI: PCI Interrupt 0000:02:0a.2[A] -> Link [LNKG] -> GSI 10 (level, low) -> IRQ 10
Dec 21 18:51:05 firewall kernel: [   56.730579] cx88[0]/2: found at 0000:02:0a.2, rev: 5, irq: 10, latency: 64, mmio: 0xd7000000
Dec 21 18:51:05 firewall kernel: [   56.730598] cx8802_probe() allocating 1 frontend(s)
Dec 21 18:51:05 firewall kernel: [   56.731007] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 11
Dec 21 18:51:05 firewall kernel: [   56.731012] ACPI: PCI Interrupt 0000:02:09.0[A] -> Link [LNKF] -> GSI 11 (level, low) -> IRQ 11
Dec 21 18:51:05 firewall kernel: [   56.870095] cx88/2: cx2388x dvb driver version 0.0.6 loaded
Dec 21 18:51:05 firewall kernel: [   56.870105] cx88/2: registering cx8802 driver, type: dvb access: shared
Dec 21 18:51:05 firewall kernel: [   56.870112] cx88[0]/2: subsystem: 11bd:0051, board: Pinnacle PCTV HD 800i [card=58]
Dec 21 18:51:05 firewall kernel: [   56.870120] cx88[0]/2: cx2388x based DVB/ATSC card
Dec 21 18:51:05 firewall kernel: [   57.032095] xc5000 0-0064: attaching existing instance
Dec 21 18:51:05 firewall kernel: [   57.060487] xc5000: Successfully identified at address 0x64
Dec 21 18:51:05 firewall kernel: [   57.060493] xc5000: Firmware has been loaded previously
Dec 21 18:51:05 firewall kernel: [   57.061819] DVB: registering new adapter (cx88[0])
Dec 21 18:51:05 firewall kernel: [   57.061825] DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
Dec 21 18:51:05 firewall kernel: [   57.947863] loop: module loaded
Dec 21 18:51:05 firewall kernel: [   57.987652] lp0: using parport0 (interrupt-driven).
Dec 21 18:51:05 firewall kernel: [   58.131191] Adding 1929208k swap on /dev/mapper/firewall-swap_1.  Priority:-1 extents:1 across:1929208k



```

So what do I need to do to get /dev/video0 back?  Is it related to this: "cx8800: Unknown symbol v4l_compat_ioctl32".

I did try searching for the message in various places, but coudln't find anything that seemed relevant.

tia ...-wayne

---

### Post by wayneschutz on 2008-12-23
24 hour bump... anyone?

---

### Post by wayneschutz on 2008-12-26
No thoughts? anyone?

---

### Post by xc3RnbFO8P on 2008-12-26
Install Kaffeine and scan channels.

---

