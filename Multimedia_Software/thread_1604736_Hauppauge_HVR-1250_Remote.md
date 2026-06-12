---
title: "Hauppauge HVR-1250 Remote"
date: 2010-10-24
forum: Multimedia Software
---

### Post by HuXu on 2010-10-24
Ubuntu 10.04 converted to Mythbuntu via mythbuntu website link

From google gathering I have attempted the following:

[LIST=1]
[*]installing v4l modules (ir_kbd_i2c)
[*][https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/454371](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/454371) (post #21) // this just made my actual keyboard not work until i changed it to say /event5
[*]modprobe ir-kbd-i2c hauppauge=1
[*]Simply setting LIRC config file to Hauppauge TV Card
[*]added "options cx23885 card=20" to custom.conf because that got my card to work
[/LIST]

Now I don't know if this is conflicting or not but I always had Enable lirc throughout this whole process in the MCC.

Here is my dmesg

```

[   15.832947] Linux video capture interface: v2.00
[   15.910268] cx23885 driver version 0.0.2 loaded
[   15.910321] cx23885 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.910417] CORE cx23885[0]: subsystem: 0070:2259, board: Hauppauge WinTV-HVR1255 [card=20,insmod option]
[   15.974477] ip_tables: (C) 2000-2006 Netfilter Core Team
[   16.002436] fb0: inteldrmfb frame buffer device
[   16.002440] registered panic notifier
[   16.002450] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   16.056912] tveeprom 1-0050: Hauppauge model 22111, rev E2F5, serial# 7316292
[   16.056917] tveeprom 1-0050: MAC address is 00-0D-FE-6F-A3-44
[   16.056920] tveeprom 1-0050: tuner model is NXP 18271C2 (idx 155, type 54)
[   16.056924] tveeprom 1-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[   16.056928] tveeprom 1-0050: audio processor is CX23888 (idx 40)
[   16.056931] tveeprom 1-0050: decoder processor is CX23888 (idx 34)
[   16.056934] tveeprom 1-0050: has no radio, has IR receiver, has no IR transmitter
[   16.056937] cx23885[0]: hauppauge eeprom: model=22111
[   16.056940] cx23885_dvb_register() allocating 1 frontend(s)
[   16.056943] cx23885[0]: cx23885 based dvb card
// cut out non relevant parts 
[   16.751781] C-Media PCI 0000:04:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   16.788750] DVB: registering new adapter (cx23885[0])
[   16.788760] DVB: registering adapter 0 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...
[   16.789344] cx23885_dev_checkrevision() Hardware revision = 0xd0
[   16.789357] cx23885[0]/0: found at 0000:03:00.0, rev: 4, irq: 17, latency: 0, mmio: 0xdfa00000
[   16.789368] cx23885 0000:03:00.0: setting latency timer to 64
[   16.789375] IRQ 17/cx23885[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   17.193509] lirc_dev: IR Remote Control driver registered, major 61 
[   17.250654] bttv: driver version 0.9.18 loaded
[   17.250661] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   17.345194] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   17.345199] tg3: eth0: Flow control is on for TX and on for RX.
[   17.350227] ivtv: Start initialization, version 1.4.1
[   17.351024] ivtv: End initialization
[   17.408626] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   17.488177] cx88/0: cx2388x v4l2 driver version 0.0.7 loaded


```

I believe ONE of my problems is I think both drivers are loading.

And lspci

```

03:00.0 Multimedia video controller: Conexant Systems, Inc. Hauppauge Inc. HDPVR-1250 model 1196 (rev 04)
04:02.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
```
 

Also I will add that irw doesn't show anything and when I run lircd -n and then irw I get this

```
lircd-0.8.6[2902]: could not get file information for /dev/lirc
lircd-0.8.6[2902]: default_init(): No such file or directory
lircd-0.8.6[2902]: Failed to initialize hardware
```

I believe I am sooooo close to getting the remote to work I can smell it but I'm just not sure where to go from here.

Let me know if you need any other information!

---

### Post by HuXu on 2010-10-25
And I'll add a bump here

---

### Post by HuXu on 2010-10-26
Dang... another bump... I'm getting lumpy here people!

---

