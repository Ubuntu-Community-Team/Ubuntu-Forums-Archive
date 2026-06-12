---
title: "I/O Errors from Samsung SATAII DVD-RAM drive"
date: 2008-12-24
forum: Multimedia Software
---

### Post by sholsinger on 2008-12-24
I'm having trouble reading DVDs from a SATAII DVD-RAM drive. See lshw output below.
```

$ sudo lshw -C disk
  *-cdrom                 
       description: DVD-RAM writer
       product: CDDVDW SH-S223Q
       vendor: TSSTcorp
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/cdrom0
       version: SB00
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted status=ready

```

Motherboard: Gigabyte GA-MA69GM-S2H with the AMD 690G north bridge and the ATI SB600 south bridge

Ubuntu 8.04 x86_64

After several attempts to play the DVD with Totem, VLC, etc... I checked to be sure that I had all the required restricted extras installed. I do. Then I thought to check for kernel errors, and voila! I/O errors. Failed reads on the disc.
```

$ sudo tail /var/log/messages
Dec 24 07:21:07 aries kernel: [150139.889650] UDF-fs: Partition marked readonly; forcing readonly mount
Dec 24 07:21:07 aries kernel: [150139.900802] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'Tron', timestamp 2002/02/11 18:17 (1ed4)
Dec 24 07:21:09 aries kernel: [150140.872538] end_request: I/O error, dev sr0, sector 5392
Dec 24 07:21:09 aries kernel: [150140.891775] end_request: I/O error, dev sr0, sector 5524
Dec 24 07:21:09 aries kernel: [150140.951287] end_request: I/O error, dev sr0, sector 226000
Dec 24 07:21:14 aries kernel: [150142.613530] end_request: I/O error, dev sr0, sector 226000
Dec 24 07:21:14 aries kernel: [150142.623556] end_request: I/O error, dev sr0, sector 226000
```

I noticed that the 'Tron' DVD is a Disney DVD with that stupid windows-only installer built into it. So, lets try another DVD. 'Training Day' was inserted... Same deal. I/O errors all over the place, can't play in Totem or VLC.

```
Dec 24 07:46:18 aries syslogd 1.5.0#1ubuntu1: restart.
Dec 24 07:50:24 aries kernel: [150950.548164] UDF-fs: Partition marked readonly; forcing readonly mount
Dec 24 07:50:24 aries kernel: [150950.575891] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'TRAINING_DAY', timestamp 2002/02/19 12:05 (1ed4)
Dec 24 07:50:25 aries kernel: [150951.798261] end_request: I/O error, dev sr0, sector 2139252
Dec 24 07:50:25 aries kernel: [150951.798268] printk: 88 messages suppressed.
```

Any ideas?

---

