---
title: "DVDs won't play"
date: 2009-05-29
forum: Multimedia Software
---

### Post by Connoro on 2009-05-29
Hi,

After searching around the Internet and the forum for a fix to no avail, I'm hoping somebody will be able to help me with my issue. I can't seem to play DVDs with my DVD drive.

The drive spins up, is recognised, the DVD icon is displayed on the desktop with the name of the DVD, hell I can browse through the VIDEO_TS folder, but nothing wants to play the DVD. I've tried MPlayer, Totem and VLC. dvd::rip also does not work.

> connor@Forest:~$ dmesg | grep CD
[    5.268883] scsi 5:0:0:0: CD-ROM            LITEON   DVD-ROM LTD163   GDHA PQ: 0 ANSI: 5
[    5.270386] Uniform CD-ROM driver Revision: 3.20
[    5.270476] sr 5:0:0:0: Attached scsi CD-ROM sr0
[    5.270838] scsi 5:0:1:0: CD-ROM            LITE-ON  LTR-24102M       4DS2 PQ: 0 ANSI: 5
[    5.274480] sr 5:0:1:0: Attached scsi CD-ROM sr1
[  150.514898] sr0: CDROM (ioctl) error, command: Xdread, Read track info 52 01 00 00 00 01 00 00 08 00
connor@Forest:~$ dmesg | grep DVD
[    5.244240] ata6.00: ATAPI: LITEON  DVD-ROM LTD163, GDHA, max UDMA/33
[    5.268883] scsi 5:0:0:0: CD-ROM            LITEON   DVD-ROM LTD163   GDHA PQ: 0 ANSI: 5

Any help? Drive works perfectly fine on Windows Vista Home Premium 64-bit, which I have on a different HDD.

---

### Post by hansdown on 2009-05-29
Hi Connoro.

Have you installed ubuntu restricted extras? Also, libdvdcss2.

They're in system> administration> synaptic package manager.

I like vlc best for movies.

---

### Post by Connoro on 2009-05-29
I too like VLC best for movies. Unfortunately, I have indeed installed libdvdread4 and libdvdcss2 and they are both the latest versions. The problem persists.

---

### Post by hansdown on 2009-05-29
The ubuntu-restricted-extras should help.

---

### Post by UbuntuNerd on 2009-05-29
you can also try this quick [guide](http://my.opera.com/ubuntunerd1/blog/how-to-play-quicktime-videos-and-other-media-with-totem) maybe you're missing something

---

