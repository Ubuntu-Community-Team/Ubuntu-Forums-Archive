---
title: "no vocals from sound card after update"
date: 2006-06-25
forum: Multimedia &amp; Video
---

### Post by ed_d on 2006-06-25
OK, this is odd. on 5.10, movies and music all worked great. Now, all I get is the music and no vocals from any plare I have tried. Also, in movies, no vocals, just everything but.

Here are some outputs:
ed@Vaal:~$ lspci
0000:00:00.0 Host bridge: Broadcom CNB20LE Host Bridge (rev 06)
0000:00:00.1 Host bridge: Broadcom CNB20LE Host Bridge (rev 06)
0000:00:02.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 0c)
0000:00:09.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)
0000:00:0a.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 06)
0000:00:0f.0 ISA bridge: Broadcom OSB4 South Bridge (rev 51)
0000:00:0f.1 IDE interface: Broadcom OSB4 IDE Controller
0000:00:0f.2 USB Controller: Broadcom OSB4/CSB5 OHCI USB Controller (rev 04)
0000:01:03.0 SCSI storage controller: Adaptec AIC-7892P U160/m (rev 02)

ed@Vaal:~$ cat /proc/asound/cards
0 [AudioPCI       ]: ENS1371 - Ensoniq AudioPCI
                     Ensoniq AudioPCI ENS1371 at 0x2240, irq 11

ed@Vaal:~$ cat /proc/asound/modules
0 snd_ens1371

Any help would be great. Was a pain even getting Dapper to work.

---

### Post by ed_d on 2006-06-26
Does no one else have this issue? I have tried everyone elses and still nothing.

---

