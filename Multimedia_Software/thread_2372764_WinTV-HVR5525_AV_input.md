---
title: "WinTV-HVR5525 AV input"
date: 2017-09-28
forum: Multimedia Software
---

### Post by liewjls on 2017-09-28
Hi,

I'm hoping i am asking in the right place, i'm new in all these video capture cards. Hope someone will able to give me right direction. I have this new Hauppage card installed and I'm using ubuntu 17.04. After googled around, i think i have installed the driver correctly and the card is registered (I think).


[HTML]~$ dmesg | grep cx23885
[    9.458893] cx23885: cx23885 driver version 0.0.4 loaded
[    9.459006] cx23885: CORE cx23885[0]: subsystem: 0070:f038, board: Hauppauge WinTV-HVR5525 [card=52,autodetected]
[    9.799080] cx23885: cx23885[0]: hauppauge eeprom: model=150329
[    9.799080] cx23885: cx23885_dvb_register() allocating 1 frontend(s)
[    9.799081] cx23885: cx23885[0]: cx23885 based dvb card
[   10.465680] dvbdev: DVB: registering new adapter (cx23885[0])
[   10.465682] cx23885 0000:02:00.0: DVB: registering adapter 0 frontend 0 (Montage Technology M88RS6000)...
[   10.465857] cx23885: cx23885_dvb_register() allocating 1 frontend(s)
[   10.465858] cx23885: cx23885[0]: cx23885 based dvb card
[   11.221713] dvbdev: DVB: registering new adapter (cx23885[0])
[   11.221714] cx23885 0000:02:00.0: DVB: registering adapter 1 frontend 0 (Silicon Labs Si2168)...
[   11.221846] cx23885: cx23885_dev_checkrevision() Hardware revision = 0xd0
[   11.221849] cx23885: cx23885[0]/0: found at 0000:02:00.0, rev: 4, irq: 17, latency: 0, mmio: 0xa1a00000
[ 1076.364907] cx23885 0000:02:00.0: invalid short VPD tag 01 at offset 1

[/HTML]

I have something in the /dev/dvb directory,
[HTML]~$ ls -lR /dev/dvb/
/dev/dvb/:
total 0
drwxr-xr-x 2 root root 120 Sep 28 15:28 adapter0
drwxr-xr-x 2 root root 120 Sep 28 15:28 adapter1

/dev/dvb/adapter0:
total 0
crw-rw----+ 1 root video 212, 1 Sep 28 15:28 demux0
crw-rw----+ 1 root video 212, 2 Sep 28 15:28 dvr0
crw-rw----+ 1 root video 212, 0 Sep 28 15:28 frontend0
crw-rw----+ 1 root video 212, 3 Sep 28 15:28 net0

/dev/dvb/adapter1:
total 0
crw-rw----+ 1 root video 212, 5 Sep 28 15:28 demux0
crw-rw----+ 1 root video 212, 6 Sep 28 15:28 dvr0
crw-rw----+ 1 root video 212, 4 Sep 28 15:28 frontend0
crw-rw----+ 1 root video 212, 7 Sep 28 15:28 net0

[/HTML]

But the problem is I don't need my hauppauge card connect to TV signal and scan for Tv channel, i need to connect to a analog TV & A/V input which i have already have a converter connect to my A/V input. I don't know how to configure my ubuntu to stream the video from /dev/video0 as I don't have /dev/video0 or /dev/videoX. I think i have missed some configuration or am i using the wrong card for that? 


Thanks.


Regards,
jenny

---

