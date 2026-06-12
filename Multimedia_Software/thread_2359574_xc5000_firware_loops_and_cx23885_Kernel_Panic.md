---
title: "xc5000 firware loops and cx23885 Kernel Panic"
date: 2017-04-25
forum: Multimedia Software
---

### Post by Crash87ss on 2017-04-25
I've had a mythbuntu system running solid for 3ish years (14.04). In the last year I began getting occasional lock-ups, requiring hard reboot. Unfortunately, these have become more frequent. I'm very lucky if the system is stable for more than a few hours. 

Current system:
Mythbuntu 16.04 with mythtv .28 (migrated from 14.04 mythtv .26 - the original stable system)
Divico Fusion HDTV Dual Express Tuner

dmesg on boot:

[    4.177441] xc5000 0-0064: creating new instance
[    4.178132] xc5000: Successfully identified at address 0x64
[    4.178133] xc5000: Firmware has not been loaded previously
[    4.244388] xc5000 1-0064: creating new instance
[    4.245081] xc5000: Successfully identified at address 0x64
[    4.245082] xc5000: Firmware has not been loaded previously
[   10.889717] xc5000: Firmware dvb-fe-xc5000-1.6.114.fw loaded and running.
[   12.789960] xc5000: Firmware dvb-fe-xc5000-1.6.114.fw loaded and running

At this point the tuner works.

From the log files I found the xc5000 firmware would get stuck in a loop, making the tuner unusable and eventually locking up the system. The log showed something to the effect of (sorry - I don't have a copy of the output now):

xc5000: i2c read failed
xc5000: Firmware has not been loaded previously
xc5000: firmware upload failed

After updating to 16.04 the system was stable for about a week before running into this issue again. 

Next step I set xc5000 no_poweroff=1. This is supposed to stop the tuner from going into an idle state, therefore not requiring a firmware reload. 
     Links to relevant threads:
       [ https://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950Q]("https://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950Q")
        [https://ubuntuforums.org/showthread.php?t=1332986]("https://ubuntuforums.org/showthread.php?t=1332986")

I confirmed this via:
 cat /sys/module/xc5000/parameters/no_poweroff
   1

This didn't seem to help, as I am still getting lockups and kernel panics. 

Watching dmesg after boot up eventually yields the following:

[  667.102109] cx23885[0]: mpeg risc op code error
[  667.102115] cx23885[0]: TS2 C - dma channel status dump
[  667.102121] cx23885[0]:   cmds: init risc lo   : 0x69ab7000
[  667.102126] cx23885[0]:   cmds: init risc hi   : 0x00000000
[  667.102132] cx23885[0]:   cmds: cdt base       : 0x000105e0
[  667.102137] cx23885[0]:   cmds: cdt size       : 0x0000000a
[  667.102142] cx23885[0]:   cmds: iq base        : 0x00010440
[  667.102148] cx23885[0]:   cmds: iq size        : 0x00000010
[  667.102153] cx23885[0]:   cmds: risc pc lo     : 0x69ab7018
[  667.102159] cx23885[0]:   cmds: risc pc hi     : 0x00000000
[  667.102164] cx23885[0]:   cmds: iq wr ptr      : 0x00004116
[  667.102170] cx23885[0]:   cmds: iq rd ptr      : 0x00004110
[  667.102175] cx23885[0]:   cmds: cdt current    : 0x00010608
[  667.102181] cx23885[0]:   cmds: pci target lo  : 0x67e048d0
[  667.102186] cx23885[0]:   cmds: pci target hi  : 0x00000000
[  667.102192] cx23885[0]:   cmds: line / byte    : 0x01630000
[  667.102197] cx23885[0]:   risc0: 0x1c0002f0 [ write sol eol count=752 ]
[  667.102205] cx23885[0]:   risc1: 0x67e045e0 [ INVALID eol irq2 irq1 23 22 21 14 count=1504 ]
[  667.102218] cx23885[0]:   risc2: 0x00000000 [ INVALID count=0 ]
[  667.102224] cx23885[0]:   risc3: 0x1c0002f0 [ write sol eol count=752 ]
[  667.102233] cx23885[0]:   (0x00010440) iq 0: 0x1c0002f0 [ write sol eol count=752 ]
[  667.102242] cx23885[0]:   iq 1: 0x67e04bc0 [ arg #1 ]
[  667.102248] cx23885[0]:   iq 2: 0x00000000 [ arg #2 ]
[  667.102253] cx23885[0]:   (0x0001044c) iq 3: 0x1c0002f0 [ write sol eol count=752 ]
[  667.102262] cx23885[0]:   iq 4: 0x67e04eb0 [ arg #1 ]
[  667.102268] cx23885[0]:   iq 5: 0x00000000 [ arg #2 ]
[  667.102273] cx23885[0]:   (0x00010458) iq 6: 0x00000000 [ INVALID count=0 ]
[  667.102281] cx23885[0]:   (0x0001045c) iq 7: 0x1c0002f0 [ write sol eol count=752 ]
[  667.102290] cx23885[0]:   iq 8: 0x67e045e0 [ arg #1 ]
[  667.102295] cx23885[0]:   iq 9: 0x00000000 [ arg #2 ]
[  667.102301] cx23885[0]:   (0x00010468) iq a: 0x1c0002f0 [ write sol eol count=752 ]
[  667.102310] cx23885[0]:   iq b: 0x67e048d0 [ arg #1 ]
[  667.102315] cx23885[0]:   iq c: 0x00000000 [ arg #2 ]
[  667.102320] cx23885[0]:   (0x00010474) iq d: 0x687f7b10 [ INVALID sol 22 21 20 19 18 cnt1 cnt0 14 13 12 count=2832 ]
[  667.102336] cx23885[0]:   (0x00010478) iq e: 0x00000000 [ INVALID count=0 ]
[  667.102343] cx23885[0]:   (0x0001047c) iq f: 0x70010000 [ jump cnt0 count=0 ]
[  667.102352] cx23885[0]:   iq 10: 0xcff1fc70 [ arg #1 ]
[  667.102358] cx23885[0]:   iq 11: 0x9d67f7af [ arg #2 ]
[  667.102361] cx23885[0]: fifo: 0x00006000 -> 0x7000
[  667.102365] cx23885[0]: ctrl: 0x00010440 -> 0x104a0
[  667.102370] cx23885[0]:   ptr1_reg: 0x000067d0
[  667.102375] cx23885[0]:   ptr2_reg: 0x00010608
[  667.102380] cx23885[0]:   cnt1_reg: 0x0000001f
[  667.102385] cx23885[0]:   cnt2_reg: 0x00000005

This repeated three times at approximately 300s intervals - then the machine kernel paniced

I tried the tuner in a different pci slot - just in case, but no luck. I might try a different MB & CPU later tonight. 

I'm not really sure what else to do from here... 

Has anyone else seen this? Any suggestions?

****Update****
Looks like the card is bad. The machine can't even fully boot with the card in place. An older pinnacle 800i card is working in its place.

---

