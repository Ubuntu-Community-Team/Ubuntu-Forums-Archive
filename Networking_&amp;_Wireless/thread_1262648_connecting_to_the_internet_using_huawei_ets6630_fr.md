---
title: "connecting to the internet using huawei ets6630 from Digi"
date: 2009-09-10
forum: Networking &amp; Wireless
---

### Post by rav0r on 2009-09-10
Digimobil Romania just released their unlimited internet plan at 384kbit/s at only 2€/month and they are offering huawei ets6630 fixed umts phones .
The problem is, I cannot find any information about these phones anywhere. 
lsusb says:
```

Bus 003 Device 002: ID 12d1:1011 Huawei Technologies Co., Ltd.

```
It seems that's another zeroCD device..

---

### Post by GeorgeVita on 2009-09-10
> **rav0r said:**
> ...```

Bus 003 Device 002: ID 12d1:1011 Huawei Technologies Co., Ltd.
```It seems that's another zeroCD device..
Hi **rav0r**,
try to use usbserial driver and check any created  /dev/ttyUSBx port.
For an updated Ubuntu 9.04:```
sudo modprobe usbserial vendor=0x12d1 product=0x1011
```
Regards,
George

---

### Post by rav0r on 2009-09-10
No chance :(

```

admmidi  cdrom7           dsp1      hidraw0  loop3    network_latency     radio0  ram5    sda         sg0       sndstat  tty11  tty22  tty33  tty44  tty55  tty9            usbdev2.1_ep00  usbdev5.1_ep00  usbdev8.1_ep00  usbmon7     vcs6   video0
adsp     cdrom8           dvd2      hidraw1  loop4    network_throughput  ram0    ram6    sda1        sg1       sr0      tty12  tty23  tty34  tty45  tty56  ttyS0           usbdev2.1_ep81  usbdev5.1_ep81  usbdev8.1_ep81  usbmon8     vcs7   watchdog
adsp1    cdrw2            dvd3      hpet     loop5    null                ram1    ram7    sda2        sg2       sr1      tty13  tty24  tty35  tty46  tty57  ttyS1           usbdev2.5_ep00  usbdev6.1_ep00  usbdev8.2_ep00  v4l         vcs8   xconsole
amidi    cdrw3            dvd6      initctl  loop6    nvidia0             ram10   ram8    sda3        sg3       sr2      tty14  tty25  tty36  tty47  tty58  ttyS2           usbdev2.5_ep02  usbdev6.1_ep81  usbdev8.2_ep81  vbi0        vcsa   zero
atmarp   cdrw6            dvdrw2    input    loop7    nvidiactl           ram11   ram9    sda4        sg4       sr3      tty15  tty26  tty37  tty48  tty59  ttyS3           usbdev2.5_ep81  usbdev6.2_ep00  usblp0          vboxdrv     vcsa1
audio    char             dvdrw3    kmem     MAKEDEV  oldmem              ram12   random  sdb         sg5       stderr   tty16  tty27  tty38  tty49  tty6   urandom         usbdev3.1_ep00  usbdev6.2_ep02  usbmon0         vboxnetctl  vcsa2
audio1   console          dvdrw6    kmsg     mapper   pktcdvd             ram13   rtc     sdb1        sg6       stdin    tty17  tty28  tty39  tty5   tty60  usb             usbdev3.1_ep81  usbdev6.2_ep81  usbmon1         vcs         vcsa3
block    core             ecryptfs  kqemu    mem      port                ram14   rtc0    sdc         sg7       stdout   tty18  tty29  tty4   tty50  tty61  usbdev1.1_ep00  usbdev3.3_ep00  usbdev6.2_ep83  usbmon2         vcs1        vcsa4
bus      cpu_dma_latency  fd        log      midi     ppp                 ram15   scd0    sdd         sg8       tty      tty19  tty3   tty40  tty51  tty62  usbdev1.1_ep81  usbdev3.3_ep04  usbdev6.3_ep00  usbmon3         vcs2        vcsa5
cdrom2   disk             fd0       loop0    mixer    psaux               ram2    scd1    sde         shm       tty0     tty2   tty30  tty41  tty52  tty63  usbdev1.4_ep00  usbdev3.3_ep83  usbdev6.3_ep81  usbmon4         vcs3        vcsa6
cdrom3   dmmidi           full      loop1    mixer1   ptmx                ram3    scd2    sequencer   snapshot  tty1     tty20  tty31  tty42  tty53  tty7   usbdev1.4_ep01  usbdev4.1_ep00  usbdev7.1_ep00  usbmon5         vcs4        vcsa7
cdrom6   dsp              fuse      loop2    net      pts                 ram4    scd3    sequencer2  snd       tty10    tty21  tty32  tty43  tty54  tty8   usbdev1.4_ep82  usbdev4.1_ep81  usbdev7.1_ep81  usbmon6         vcs5        vcsa8

```

---

### Post by rav0r on 2009-09-10
In Win Xp, the device monitoring studio shows the same product ID for the USB Mass Storage Device, for the ETS modem and ETS PC UI Interface so I belive it will be damn difficult to know what mode the phone is in.

---

