---
title: "[drm:edid_is_valid] *ERROR* Raw EDID"
date: 2011-03-25
forum: Multimedia Software
---

### Post by skthetwo on 2011-03-25
I'd been getting force logged off -with no session to connect back to - since I have a cluster that runs for hrs this sort of forced logged off is quite unacceptable.  

Ubunutu 10.04 LTS 64bit, Biostar TA790GXB3 is the MB.   Full error signature at the bottom of this post:

it just "felt" like it was a CRT problem.. Not much in the logs except this message above was persistent - every few seconds ending up with :

radeon 0000:01:05.0: VGA-1: EDID invalid.

Huh !  I don't have a VGA-1 ( just the one onboard GFX790 video chip.

googling I know that EDID is Extended Display Identification and I know that drm is directed rendering manager. ALso the monitors option in preferences coudln't identify the monitor.  I was using an old CRT connected via VGA so I replaced it a 32ii LCD(NIKO) - DVI connection the problem disappeared. ALso in Preferences its identified 

Next I used a Micron VGA connected CRT - again no problem !  Again in Preferences->Monitors  the CRT is identified correctly.

Time and many uses later will I be able to tell is this was indeed the forced log off problem, ( there is an associated trace about Xorg process crashing )  but anybody care to comment on the possibilities ( or non-possibilities).

Can I bypass the EDID biz ? by doing something to that old IBM CRT monitor ? by using PowerStrip ?
Since I do have a running system that is running under load for 3 hours now, seemingly... this is just out of curioisity and to prepare myself for the possibility that this wasn't the problem. 

============= Error signature ==========
Mar 24 17:54:53 thermaltake kernel: [   31.024302] [drm:edid_is_valid] *ERROR* Raw EDID:
Mar 24 17:54:53 thermaltake kernel: [   31.024303] <3>ff 00 00 00 00 00 00 00 24 4d 96 19 01 01 01 01  ........$M......
Mar 24 17:54:53 thermaltake kernel: [   31.024305] <3>18 0a 01 01 6e 21 18 96 e8 0c c9 a0 57 47 9b 27  ....n!......WG.'
Mar 24 17:54:53 thermaltake kernel: [   31.024306] <3>12 48 4c ef cf 00 31 59 45 59 61 59 71 59 a9 4f  .HL...1YEYaYqY.O
Mar 24 17:54:53 thermaltake kernel: [   31.024307] <3>81 99 01 01 01 01 90 14 c0 2c 31 11 1c 20 0c 6c  .........,1.. .l
Mar 24 17:54:53 thermaltake kernel: [   31.024309] <3>1a 00 38 ea 10 00 00 1a 00 00 00 fc 00 49 42 4d  ..8..........IBM
Mar 24 17:54:53 thermaltake kernel: [   31.024310] <3>20 50 37 36 0a 20 20 20 20 20 00 00 00 fd 00 30   P76.     .....0
Mar 24 17:54:53 thermaltake kernel: [   31.024311] <3>78 1e 5e 19 00 0a 20 20 20 20 20 20 00 00 00 ff  x.^...      ....
Mar 24 17:54:53 thermaltake kernel: [   31.024312] <3>00 35 35 46 34 31 38 33 0a 20 20 20 20 20 00 2a  .55F4183.     .*
Mar 24 17:54:53 thermaltake kernel: [   31.024313] 
Mar 24 17:54:53 thermaltake kernel: [   31.074644] [drm:edid_is_valid] *ERROR* Raw EDID:
Mar 24 17:54:53 thermaltake kernel: [   31.074645] <3>ff 00 00 00 00 00 00 00 24 4d 96 19 01 01 01 01  ........$M......
Mar 24 17:54:53 thermaltake kernel: [   31.074646] <3>18 0a 01 01 6e 21 18 96 e8 0c c9 a0 57 47 9b 27  ....n!......WG.'
Mar 24 17:54:53 thermaltake kernel: [   31.074648] <3>12 48 4c ef cf 00 31 59 45 59 61 59 71 59 a9 4f  .HL...1YEYaYqY.O
Mar 24 17:54:53 thermaltake kernel: [   31.074649] <3>81 99 01 01 01 01 90 14 c0 2c 31 11 1c 20 0c 6c  .........,1.. .l
Mar 24 17:54:53 thermaltake kernel: [   31.074650] <3>1a 00 38 ea 10 00 00 1a 00 00 00 fc 00 49 42 4d  ..8..........IBM
Mar 24 17:54:53 thermaltake kernel: [   31.074651] <3>20 50 37 36 0a 20 20 20 20 20 00 00 00 fd 00 30   P76.     .....0
Mar 24 17:54:53 thermaltake kernel: [   31.074653] <3>78 1e 5e 19 00 0a 20 20 20 20 20 20 00 00 00 ff  x.^...      ....
Mar 24 17:54:53 thermaltake kernel: [   31.074654] <3>00 35 35 46 34 31 38 33 0a 20 20 20 20 20 00 2a  .55F4183.     .*
Mar 24 17:54:53 thermaltake kernel: [   31.074655] 
Mar 24 17:54:53 thermaltake kernel: [   31.074656] radeon 0000:01:05.0: VGA-1: EDID invalid.

---

### Post by skthetwo on 2011-03-26
One day and an overnight of a heavy computational load later.. its still on - no forced logoffs. Tentatively I think the way an aspect of the kernel is dealing with EDIDs was the problem ( until it isn't ).

---

### Post by Aacron on 2011-04-22
I don't understand why this is compiled into the kernel anyhow.  Especially in the server kernel, as generally we aren't running GUIs -- just the terminal.  Doesn't something like this belong in a module, or perhaps in Xorg, instead of a place where it is generally useless, and could cause issues?

We don't need the kitchen sink in the kernel.

---

