---
title: "high-performance drive cache?"
date: 2008-11-05
forum: Mythbuntu
---

### Post by tedder on 2008-11-05
So I'd like to use a 10,000rpm drive to record my shows, then use a slower-speed, high-capacity drive to archive the shows. The high-speed drive will be small (100gb), while the archive drive(s) will be large (1tb).

How can I do this within mythbuntu or ubuntu? I mean, AFAICT mythtv doesn't let you distinguish between drives.

An alternate would be if there is some way to do this with hardware- for instance, is there such a thing as a SATA controller card that has 1gb of memory on it to do very intelligent caching?

I hope my question is clear enough.

---

### Post by ian dobson on 2008-11-05
Hi,

Why do you want that? I have a 3 x 1Tb raid 5 array running mdadm (software raid) and I have no problems recording 3 SD and 1 HD program at the same time.

Regards
Ian Dobson

---

### Post by tedder on 2008-11-05
Ian, do you have it set up as a LVM/JBOD, or some sort of RAID?

I'm recording two HD and two SD streams, plus commercial scanning (one thread at a time). CPU is fine, but it seems I have some HD i/o issues.

---

### Post by ian dobson on 2008-11-05
Hi,

The setup I have is :-

3 x 1Tb 32Mb cache drives in a RAID5 array using mdadm.
Running on a Q6600 with 4Gb ram on a i965 chipset motherboard.

I think the 4Gb ram makes a ver big difference as the kernel is able to cache most of the recording data to disk activivy isn't that much.

I commercial scan up to 3 recordings at the same time.

Regards
Ian Dobson

---

### Post by tedder on 2008-11-07
Thanks for the info. Can you pull iostat when your system is going full blast?

```
Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
(snip)
sdc               0.00    10.27    0.13   48.13     1.07  7957.33   164.88     0.26    5.38   1.71   8.27

```

Look at sdc- note the writes are around 8000 sectors for second. I don't even know how many writes I can get per second out of a SATA setup.

I'm using XFS.

Later, I saw this:
```
sdc              12.93     4.00  136.87   41.20 37454.93  4921.60   237.98     1.48    8.33   3.35  59.60
```

---

### Post by ian dobson on 2008-11-07
Hi,

Here's my iostat for 4 recordings at once, 1 SD DVB-C, 1 HD DVB-C and 2 Analog channels (PVR-500) while commflagging 3 programs.

```

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.46   72.84    1.16    0.19    0.00   25.35

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               0.02     3.66    0.22    1.74     4.70    43.21    24.47     0.01    3.86   1.33   0.26
sda1              0.02     3.66    0.22    1.74     4.69    43.21    24.48     0.01    3.86   1.33   0.26
sda2              0.00     0.00    0.00    0.00     0.00     0.00     2.00     0.00   50.00  50.00   0.00
sda5              0.00     0.00    0.00    0.00     0.00     0.00    23.47     0.00    7.29   6.76   0.00
sdb               5.46    31.24    2.38    6.12   138.05   304.80    52.08     0.16   18.35   4.22   3.59
sdb1              5.46    31.24    2.38    6.12   138.05   304.80    52.09     0.16   18.35   4.22   3.59
sdc               0.00     0.00    0.00    0.00     0.01     0.00    20.77     0.00    1.98   1.39   0.00
sdc1              0.00     0.00    0.00    0.00     0.01     0.00    25.03     0.00    1.51   0.86   0.00
sdd               5.43    31.34    2.27    6.24   137.00   306.61    52.14     0.21   25.02   4.63   3.94
sdd1              5.43    31.34    2.27    6.24   137.00   306.61    52.14     0.21   25.02   4.63   3.94
sde               5.43    31.29    2.32    6.22   137.30   306.06    51.93     0.14   16.90   3.91   3.33
sde1              5.43    31.29    2.32    6.22   137.30   306.06    51.93     0.14   16.90   3.91   3.33
md0               0.00     0.00    3.67   63.34   255.50   506.71    11.37     0.00    0.00   0.00   0.00

```

Encoder status
Encoder 3 is local on alpha2 and is recording: 'Kindermädchen für Papa gesucht' on 3sat. This recording will end at 3:33 PM.
Encoder 4 is local on alpha2 and is not recording.
Encoder 5 is local on alpha2 and is recording: 'Die Kinderklinik 3 - Ein Licht in dunkler Nacht' on ANIXE HD. This recording will end at 3:33 PM.
Encoder 6 is local on alpha2 and is not recording.
Encoder 11 is local on alpha2 and is recording: 'Serengeti 24' on BBC Prime. This recording will end at 4:08 PM.
Encoder 12 is local on alpha2 and is recording: 'Swiss DayQuiz' on 3+. This recording will end at 5:08 PM.

Job Queue
Jobs currently in Queue or recently ended: 

Fri 11/7 3:22 PM - Kindermädchen für Papa gesucht - Flag Commercials
Fri 11/7 3:22 PM - Die Kinderklinik 3 - Ein Licht in dunkler Nacht - Flag Commercials
Fri 11/7 3:24 PM - Swiss DayQuiz - Flag Commercials

Note md0 is my RAID5 array.

Regards
Ian Dobson

---

