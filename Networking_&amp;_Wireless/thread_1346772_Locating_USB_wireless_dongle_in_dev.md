---
title: "Locating USB wireless dongle in /dev"
date: 2009-12-05
forum: Networking &amp; Wireless
---

### Post by ClusterOne on 2009-12-05
Hello,

I am trying to locate a netgear wg111v2 usb wireless dongle under /dev. I first section of test copied from the terminal is before the usb is inserted, and the second section is after. Ubuntu is detecting the dongle and I can see wireless networks using the network manager. 

```


root@UbUSB:/dev# ls -attr
pts               ram15               tty23  tty63    vcsa2       sequencer2
null              ram14               tty19  tty62    vcs3        sequencer
.initramfs-tools  tty49               tty14  tty60    vcs2        log
usbmon1           tty48               tty10  tty54    vcsa4       mixer
bus               tty45               tty0   tty52    vcs4        dsp
usbmon2           tty41               ram8   tty51    vcsa6       audio
ram4              tty38               ram7   sg1      vcsa5       adsp
port              tty35               ram6   vcsa     vcs6        console
pktcdvd           tty33               ram13  usbmon0  vcs5        mixer1
oldmem            tty32               ram1   tty7     vcsa8       snd
mcelog            tty30               psaux  tty61    vcs8        mixer2
fuse              tty27               ppp    tty59    sg3         urandom
cpu_dma_latency   tty25               loop0  tty58    sdc         tty5
binder            tty21               zero   tty57    sdc4        tty4
tty46             tty17               tty47  tty56    sdc3        tty2
tty44             tty12               tty37  tty55    sdc2        tty6
tty42             rfkill              tty29  tty53    sdc6        tty3
tty40             random              ram9   ram5     sdc5        .udev
tty39             ram3                mem    sg2      sdc1        vcsa7
tty36             network_throughput  loop7  sg0      block       vcs7
tty34             network_latency     loop5  fd0      .initramfs  char
tty31             mapper              loop4  sr0      stdout      ati
tty28             loop1               loop3  scd0     stderr      .
tty26             hpet                kmsg   sda      fd          tty8
tty24             ecryptfs            full   hidraw1  core        tty1
tty22             ttyS3               ram12  sdb      stdin       shm
tty20             ttyS2               ram11  sda1     sndstat     tty
tty18             ttyS1               ram10  disk     net         ..
tty16             ttyS0               ram0   sdb1     .blkid.tab  ptmx
tty15             rtc0                tty50  hidraw0  dvdrw
tty13             rtc                 vcsa1  usb      dvd
tty11             loop6               vcs1   hidraw3  cdrw
snapshot          loop2               vcs    hidraw2  cdrom
ram2              tty43               tty9   vcsa3    input



```
After usb is inserted. 

```


root@UbUSB:/dev# ls -attr
pts               ram15               tty23  tty63    vcsa2       sequencer2
null              ram14               tty19  tty62    vcs3        sequencer
.initramfs-tools  tty49               tty14  tty60    vcs2        log
usbmon1           tty48               tty10  tty54    vcsa4       mixer
bus               tty45               tty0   tty52    vcs4        dsp
usbmon2           tty41               ram8   tty51    vcsa6       audio
ram4              tty38               ram7   sg1      vcsa5       adsp
port              tty35               ram6   vcsa     vcs6        console
pktcdvd           tty33               ram13  usbmon0  vcs5        mixer1
oldmem            tty32               ram1   tty7     vcsa8       snd
mcelog            tty30               psaux  tty61    vcs8        mixer2
fuse              tty27               ppp    tty59    sg3         urandom
cpu_dma_latency   tty25               loop0  tty58    sdc         tty5
binder            tty21               zero   tty57    sdc4        tty4
tty46             tty17               tty47  tty56    sdc3        tty2
tty44             tty12               tty37  tty55    sdc2        tty6
tty42             rfkill              tty29  tty53    sdc6        tty3
tty40             random              ram9   ram5     sdc5        vcsa7
tty39             ram3                mem    sg2      sdc1        vcs7
tty36             network_throughput  loop7  sg0      block       ati
tty34             network_latency     loop5  fd0      .initramfs  .
tty31             mapper              loop4  sr0      stdout      tty8
tty28             loop1               loop3  scd0     stderr      tty1
tty26             hpet                kmsg   sda      fd          tty
tty24             ecryptfs            full   hidraw1  core        ..
tty22             ttyS3               ram12  sdb      stdin       shm
tty20             ttyS2               ram11  sda1     sndstat     char
tty18             ttyS1               ram10  disk     net         .udev
tty16             ttyS0               ram0   sdb1     .blkid.tab  ptmx
tty15             rtc0                tty50  hidraw0  dvdrw
tty13             rtc                 vcsa1  usb      dvd
tty11             loop6               vcs1   hidraw3  cdrw
snapshot          loop2               vcs    hidraw2  cdrom
ram2              tty43               tty9   vcsa3    input


```
Many thanks.

---

### Post by uncaspi on 2009-12-05
lsusb -v

---

### Post by uncaspi on 2009-12-05
It seems this is not listed in /dev
Besides lsusb -v you can also plug in the dongle and look in the log files for information. dmesg and pico /var/log/messages

---

### Post by ClusterOne on 2009-12-05
As its a serial usb device I thought it should mount as ttyUSB0.:o


tail /var/log/messages
```


root@UbUSB:/home/matthew# tail /var/log/messages
Dec  5 20:47:09 UbUSB kernel: [ 1434.044992] p54: rx_mtu reduced from 3240 to 2384
Dec  5 20:47:09 UbUSB kernel: [ 1434.044994] phy1: FW rev 2.13.24.0 - Softmac protocol 5.9
Dec  5 20:47:09 UbUSB kernel: [ 1434.044995] phy1: cryptographic accelerator WEP:YES, TKIP:YES, CCMP:YES
Dec  5 20:47:10 UbUSB kernel: [ 1435.046086] phy1: hwaddr 00:0f:b5:92:a5:e4, MAC:isl3887 RF:Frisbee
Dec  5 20:47:10 UbUSB kernel: [ 1435.051483] Registered led device: p54-phy1::assoc
Dec  5 20:47:10 UbUSB kernel: [ 1435.051494] Registered led device: p54-phy1::tx
Dec  5 20:47:10 UbUSB kernel: [ 1435.051506] Registered led device: p54-phy1::rx
Dec  5 20:47:10 UbUSB kernel: [ 1435.051517] Registered led device: p54-phy1::radio
Dec  5 20:47:10 UbUSB kernel: [ 1435.051522] usb 1-10: is registered as 'phy1'
Dec  5 20:47:10 UbUSB kernel: [ 1435.057447] udev: renamed network interface wlan0 to wlan1


```
dmesg

```


  204.644016] usb 1-10: new high speed USB device using ehci_hcd and address 5
[  204.781518] usb 1-10: configuration #1 chosen from 1 choice
[  204.876545] cfg80211: Calling CRDA to update world regulatory domain
[  205.049570] cfg80211: World regulatory domain updated:
[  205.049572]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  205.049575]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  205.049577]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  205.049579]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  205.049581]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  205.049582]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  205.092514] usb 1-10: reset high speed USB device using ehci_hcd and address 5
[  205.226081] usb 1-10: firmware: requesting isl3887usb
[  205.300395] phy0: p54 detected a LM87 firmware
[  205.300397] p54: rx_mtu reduced from 3240 to 2384
[  205.300399] phy0: FW rev 2.13.24.0 - Softmac protocol 5.9
[  205.300401] phy0: cryptographic accelerator WEP:YES, TKIP:YES, CCMP:YES
[  206.300709] phy0: hwaddr 00:0f:b5:92:a5:e4, MAC:isl3887 RF:Frisbee
[  206.364940] phy0: Selected rate control algorithm 'minstrel'
[  206.365435] Registered led device: p54-phy0::assoc
[  206.365446] Registered led device: p54-phy0::tx
[  206.365457] Registered led device: p54-phy0::rx
[  206.365468] Registered led device: p54-phy0::radio
[  206.365477] usb 1-10: is registered as 'phy0'
[  206.365490] usbcore: registered new interface driver p54usb
[  206.403060] udev: renamed network interface wlan0 to wlan1
matthew@UbUSB:~$ 



```

Thanks again.

---

### Post by ClusterOne on 2009-12-05
Ok, I ran ls attr @ /dev again, in Backtrack 4 and got usbdev1.5_ep00, usbdev1.5_ep01, usbdev1.5_ep02 etc.

Any idea why it isn't ttyUSB0?

Many thanks!

---

