---
title: "Ubuntu Won't play DVD's, or else rarely does."
date: 2012-10-13
forum: Multimedia Software
---

### Post by shizz on 2012-10-13
The reason I say rarely does is that after a few times of opening and closing the tray and various combinations of having it open or closed on bootup /log in, it read the disc once.

The usual scenario is that I close the tray, hear two noises as it sounds like the tray is about to spool up, but then nothing happens.

Any ideas?

I've googled this a few times and nothing has helped. I seem to have all the packages installed etc.

Any help would be greatly appreciated.

Thanks.

---

### Post by ajgreeny on 2012-10-13
If you really do have all the software needed including libdvdcss2 it sounds as if it must be a hardware problem.

I once had exactly that problem where my drive would read some DVDs easily, but others just tried again and again to spin up and start reading, then just stopped.  A new drive solved the problem.

---

### Post by shizz on 2012-10-13
I find it hard to believe that it is a hardware problem due to the fact that it reads and writes data to DVD's fine. I can also view the said DVD on windows with it.

Also, it has played this DVD before so I'm at a loss as to what is wrong.

---

### Post by shizz on 2012-10-13
> dmesg | grep -i scsi
[    1.772504] SCSI subsystem initialized
[    2.122274] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    2.384580] scsi0 : ahci
[    2.384659] scsi1 : ahci
[    2.384721] scsi2 : ahci
[    2.384783] scsi3 : ahci
[    2.384841] scsi4 : ahci
[    2.384898] scsi5 : ahci
[    2.841386] scsi 0:0:0:0: Direct-Access     ATA      ST9640320AS      0002 PQ: 0 ANSI: 5
[    2.841526] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.844918] scsi 1:0:0:0: CD-ROM            Slimtype BD  E  DS4E1S    EA2B PQ: 0 ANSI: 5
[    2.849551] sr0: scsi3-mmc drive: 24x/1x writer dvd-ram cd/rw xa/form2 cdda pop-up
[    2.849784] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.849902] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.895651] sd 0:0:0:0: [sda] Attached SCSI disk


I thought that this may help. I'm not sure how to decipher it.

---

### Post by oldos2er on 2012-10-13
Can you post the output of ```
ls /usr/lib/libdvd*
```

---

### Post by shizz on 2012-10-13
> ls /usr/lib/libdvd*
/usr/lib/libdvdcss.so.2          /usr/lib/libdvdnav.so.4
/usr/lib/libdvdcss.so.2.1.0      /usr/lib/libdvdnav.so.4.2.0
/usr/lib/libdvdnavmini.so.4      /usr/lib/libdvdread.so.4
/usr/lib/libdvdnavmini.so.4.2.0  /usr/lib/libdvdread.so.4.2.0


Thanks again.

---

### Post by shizz on 2012-10-14
Just thought I'd add that the drive randomly decided to read the disc as I turned on my laptop this morning. Strange.

---

### Post by oldos2er on 2012-10-14
You've got all the codecs you need. What program are you using to watch the dvd?

---

### Post by shizz on 2012-10-14
> **oldos2er said:**
> You've got all the codecs you need. What program are you using to watch the dvd?

VLC. But it's not the program that is the problem. Usually when I put a disc in it starts to whirr up and a box will pop up asking what do I want to do with it. This wasn't happening until I turned it on this morning. The likely hood is, if I turn my laptop off and on again it wont open again.

---

### Post by Future Warthog on 2012-10-14
Are you using 12.04 Precise Pangolin? If so try this site:
[25 Things I did after installing Ubuntu 12.04]("http://www.techdrivein.com/2012/06/25-things-i-did-after-installing-ubuntu.html")
It has a fix for this exact problem (if on 12.04) along with plenty of other great stuff.
Worked for me :D

Best of luck!
-Packpatfan

---

