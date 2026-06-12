---
title: "Problem with SATA discs"
date: 2011-04-16
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by martijntje on 2011-04-16
I have been running natty for about two weeks now. At first it worked fine, but now I am getting some IO problems. It always happens when watching movies, the HD light stays completely on.

Then, after a while I get some messages in my log and the system continues.

```
Apr 16 23:34:59 martijntje kernel: [16890.080244] ata1.00: exception Emask 0x0 SAct 0x1fff SErr 0x0 action 0x6 frozen
Apr 16 23:34:59 martijntje kernel: [16890.080484] ata1.00: failed command: WRITE FPDMA QUEUED
Apr 16 23:34:59 martijntje kernel: [16890.080656] ata1.00: cmd 61/08:00:58:fb:87/00:00:04:00:00/40 tag 0 ncq 4096 out
Apr 16 23:34:59 martijntje kernel: [16890.080659]          res 40/00:00:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
Apr 16 23:34:59 martijntje kernel: [16890.081104] ata1.00: status: { DRDY }
Apr 16 23:34:59 martijntje kernel: [16890.081220] ata1.00: failed command: WRITE FPDMA QUEUED
Apr 16 23:34:59 martijntje kernel: [16890.081388] ata1.00: cmd 61/08:08:60:fb:87/00:00:04:00:00/40 tag 1 ncq 4096 out
Apr 16 23:34:59 martijntje kernel: [16890.081391]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Apr 16 23:34:59 martijntje kernel: [16890.081834] ata1.00: status: { DRDY }
Apr 16 23:34:59 martijntje kernel: [16890.081949] ata1.00: failed command: WRITE FPDMA QUEUED
Apr 16 23:34:59 martijntje kernel: [16890.082117] ata1.00: cmd 61/08:10:68:fb:87/00:00:04:00:00/40 tag 2 ncq 4096 out
Apr 16 23:34:59 martijntje kernel: [16890.082120]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Apr 16 23:34:59 martijntje kernel: [16890.082563] ata1.00: status: { DRDY }
Apr 16 23:34:59 martijntje kernel: [16890.082678] ata1.00: failed command: WRITE FPDMA QUEUED
Apr 16 23:34:59 martijntje kernel: [16890.082845] ata1.00: cmd 61/08:18:70:fb:87/00:00:04:00:00/40 tag 3 ncq 4096 out
Apr 16 23:34:59 martijntje kernel: [16890.082848]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Apr 16 23:34:59 martijntje kernel: [16890.083292] ata1.00: status: { DRDY }
Apr 16 23:34:59 martijntje kernel: [16890.087656] ata1.00: failed command: WRITE FPDMA QUEUED
Apr 16 23:34:59 martijntje kernel: [16890.092079] ata1.00: cmd 61/08:20:78:fb:87/00:00:04:00:00/40 tag 4 ncq 4096 out
Apr 16 23:34:59 martijntje kernel: [16890.092082]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Apr 16 23:34:59 martijntje kernel: [16890.109918] ata1.00: status: { DRDY }
Apr 16 23:34:59 martijntje kernel: [16890.109923] ata1.00: failed command: WRITE FPDMA QUEUED
Apr 16 23:34:59 martijntje kernel: [16890.109936] ata1.00: cmd 61/08:28:80:fb:87/00:00:04:00:00/40 tag 5 ncq 4096 out
Apr 16 23:34:59 martijntje kernel: [16890.109939]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Apr 16 23:34:59 martijntje kernel: [16890.109944] ata1.00: status: { DRDY }
Apr 16 23:34:59 martijntje kernel: [16890.109949] ata1.00: failed command: WRITE FPDMA QUEUED
Apr 16 23:34:59 martijntje kernel: [16890.109960] ata1.00: cmd 61/08:30:88:fb:87/00:00:04:00:00/40 tag 6 ncq 4096 out
Apr 16 23:34:59 martijntje kernel: [16890.109963]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Apr 16 23:34:59 martijntje kernel: [16890.109968] ata1.00: status: { DRDY }
Apr 16 23:34:59 martijntje kernel: [16890.109972] ata1.00: failed command: WRITE FPDMA QUEUED
Apr 16 23:34:59 martijntje kernel: [16890.109984] ata1.00: cmd 61/08:38:90:fb:87/00:00:04:00:00/40 tag 7 ncq 4096 out
Apr 16 23:34:59 martijntje kernel: [16890.109986]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Apr 16 23:34:59 martijntje kernel: [16890.109991] ata1.00: status: { DRDY }
Apr 16 23:34:59 martijntje kernel: [16890.109996] ata1.00: failed command: WRITE FPDMA QUEUED
Apr 16 23:34:59 martijntje kernel: [16890.110007] ata1.00: cmd 61/08:40:98:fb:87/00:00:04:00:00/40 tag 8 ncq 4096 out
Apr 16 23:34:59 martijntje kernel: [16890.110010]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Apr 16 23:34:59 martijntje kernel: [16890.110028] ata1.00: status: { DRDY }
Apr 16 23:34:59 martijntje kernel: [16890.110035] ata1.00: failed command: WRITE FPDMA QUEUED
Apr 16 23:34:59 martijntje kernel: [16890.110046] ata1.00: cmd 61/08:48:a0:fb:87/00:00:04:00:00/40 tag 9 ncq 4096 out
Apr 16 23:34:59 martijntje kernel: [16890.110049]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Apr 16 23:34:59 martijntje kernel: [16890.110054] ata1.00: status: { DRDY }
Apr 16 23:34:59 martijntje kernel: [16890.110059] ata1.00: failed command: WRITE FPDMA QUEUED
Apr 16 23:34:59 martijntje kernel: [16890.110070] ata1.00: cmd 61/08:50:a8:fb:87/00:00:04:00:00/40 tag 10 ncq 4096 out
Apr 16 23:34:59 martijntje kernel: [16890.110073]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Apr 16 23:34:59 martijntje kernel: [16890.110078] ata1.00: status: { DRDY }
Apr 16 23:34:59 martijntje kernel: [16890.110082] ata1.00: failed command: WRITE FPDMA QUEUED
Apr 16 23:34:59 martijntje kernel: [16890.110094] ata1.00: cmd 61/08:58:b0:fb:87/00:00:04:00:00/40 tag 11 ncq 4096 out
Apr 16 23:34:59 martijntje kernel: [16890.110097]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Apr 16 23:34:59 martijntje kernel: [16890.110101] ata1.00: status: { DRDY }
Apr 16 23:34:59 martijntje kernel: [16890.110106] ata1.00: failed command: READ FPDMA QUEUED
Apr 16 23:34:59 martijntje kernel: [16890.110117] ata1.00: cmd 60/08:60:40:f7:4b/00:00:00:00:00/40 tag 12 ncq 4096 in
Apr 16 23:34:59 martijntje kernel: [16890.110120]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Apr 16 23:34:59 martijntje kernel: [16890.110125] ata1.00: status: { DRDY }
Apr 16 23:34:59 martijntje kernel: [16890.110134] ata1: hard resetting link
Apr 16 23:34:59 martijntje kernel: [16890.660086] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Apr 16 23:34:59 martijntje kernel: [16890.660646] ata1.00: configured for UDMA/133
Apr 16 23:34:59 martijntje kernel: [16890.680189] ata1.00: device reported invalid CHS sector 0
Apr 16 23:34:59 martijntje kernel: [16890.680198] ata1.00: device reported invalid CHS sector 0
Apr 16 23:34:59 martijntje kernel: [16890.680204] ata1.00: device reported invalid CHS sector 0
Apr 16 23:34:59 martijntje kernel: [16890.680210] ata1.00: device reported invalid CHS sector 0
Apr 16 23:34:59 martijntje kernel: [16890.680215] ata1.00: device reported invalid CHS sector 0
Apr 16 23:34:59 martijntje kernel: [16890.680220] ata1.00: device reported invalid CHS sector 0
Apr 16 23:34:59 martijntje kernel: [16890.680225] ata1.00: device reported invalid CHS sector 0
Apr 16 23:34:59 martijntje kernel: [16890.680230] ata1.00: device reported invalid CHS sector 0
Apr 16 23:34:59 martijntje kernel: [16890.680235] ata1.00: device reported invalid CHS sector 0
Apr 16 23:34:59 martijntje kernel: [16890.680240] ata1.00: device reported invalid CHS sector 0
Apr 16 23:34:59 martijntje kernel: [16890.680245] ata1.00: device reported invalid CHS sector 0
Apr 16 23:34:59 martijntje kernel: [16890.680250] ata1.00: device reported invalid CHS sector 0
Apr 16 23:34:59 martijntje kernel: [16890.680256] ata1.00: device reported invalid CHS sector 0
Apr 16 23:34:59 martijntje kernel: [16890.680292] ata1: EH complete
```

Anybody got a clue what to do about this?

---

### Post by cariboo on 2011-04-16
Have a look at this bug #[lpbug]550559[/lpbug]

---

### Post by VMC on 2011-04-16
> **martijntje said:**
> I have been running natty for about two weeks now. At first it worked fine, but now I am getting some IO problems. It always happens when watching movies, the HD light stays completely on.

Then, after a while I get some messages in my log and the system continues.
...

Anybody got a clue what to do about this?

Running the _Disk Utility_, what does the _SMART Data_ say?

---

### Post by martijntje on 2011-04-17
It's the bug cariboo describes. The S.M.A.R.T. report says all three discs are healthy.

---

### Post by dino99 on 2011-04-17
is there an other bios setting than "ahci", like "compatible" to switch on ?
have you the same issue id ssd & hdd order is switched ?
what about the hdd software/driver, if exist, can it be updated ? Is there thread(s)/issue(s) known on the hdd forum ?

---

### Post by ikt on 2011-04-17
> **martijntje said:**
> Anybody got a clue what to do about this?

What motherboard have you got?

---

