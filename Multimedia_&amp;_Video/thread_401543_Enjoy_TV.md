---
title: "Enjoy TV"
date: 2007-04-04
forum: Multimedia &amp; Video
---

### Post by zell77 on 2007-04-04
i have this Tvcard...that i can't work on...

i search for card and tuner number...i found and:

```
dani@linux:~$ sudo modprobe -r saa7134-alsa
dani@linux:~$ sudo modprobe -r saa7134
dani@linux:~$ lsmod | grep saa71
dani@linux:~$ sudo modprobe saa7134 card=59 tuner=54
dani@linux:~$ dmesg | grep saa
[17179816.700000] saa7130/34: v4l2 driver version 0.2.14 loaded
[17179816.704000] saa7133[0]: found at 0000:02:0a.0, rev: 208, irq: 217, latency: 32, mmio: 0xf6026000
[17179816.704000] saa7133[0]: subsystem: 1131:0000, board: Medion 7134 [card=12,insmod option]
[17179816.704000] saa7133[0]: board init: gpio is 40
[17179816.820000] tda9887 5-004b: chip found @ 0x96 (saa7133[0])
[17179816.832000] saa7133[0]: Huh, no eeprom present (err=-5)?
[17179816.832000] saa7133[0] Tuner type is 54
[17179816.880000] saa7133[0]: registered device video0 [v4l2]
[17179816.880000] saa7133[0]: registered device vbi0
[17179816.880000] saa7133[0]: registered device radio0
[17180884.856000] saa7130/34: v4l2 driver version 0.2.14 loaded
[17180884.860000] saa7133[0]: found at 0000:02:0a.0, rev: 208, irq: 217, latency: 32, mmio: 0xf6026000
[17180884.860000] saa7133[0]: subsystem: 1131:0000, board: Kworld/Tevion V-Stream Xpert TV PVR7134 [card=59,insmod option]
[17180884.860000] saa7133[0]: board init: gpio is 40
[17180884.996000] input: saa7134 IR (Kworld/Tevion V-Str as /class/input/input4
[17180885.224000] tda9887 5-004b: chip found @ 0x96 (saa7133[0])
[17180885.244000] saa7133[0]: Huh, no eeprom present (err=-5)?
[17180885.284000] saa7133[0]: registered device video0 [v4l2]
[17180885.284000] saa7133[0]: registered device vbi0
[17180885.284000] saa7133[0]: registered device radio0
dani@linux:~$ tvtime-scanner
Reading configuration from /etc/tvtime/tvtime.xml
Scanning using TV standard PAL.
Scanning from  44,00 MHz to 958,00 MHz.
Checking  50,25 MHz:  - No signal                     
dani@linux:~$ scantv

please select your TV norm
   0: PAL
   1: PAL-BG
   2: PAL-I
   3: PAL-DK
   4: NTSC
   5: SECAM
   6: PAL-M
   7: PAL-Nc
   8: PAL-60
nr ? 1

please select a frequency table
   0: us-bcast
   1: us-cable
   2: us-cable-hrc
   3: japan-bcast
   4: japan-cable
   5: europe-west
   6: europe-east
   7: italy
   8: newzealand
   9: australia
  10: ireland
  11: france
  12: china-bcast
  13: southafrica
  14: argentina
  15: australia-optus
  16: russia
nr ? 7
[global]
freqtab = italy

[defaults]
input = Television
norm = PAL-BG


scanning channel list italy...
A    ( 53.75 MHz): no station
B    ( 62.25 MHz): no station
C    ( 82.25 MHz): no station
D    (175.25 MHz): no station
E    (183.75 MHz): no station
F    (192.25 MHz): no station
G    (201.25 MHz): no station
H    (210.25 MHz): no station
H1   (217.25 MHz): no station
H2   (224.25 MHz): no station
21   (471.25 MHz): no station
22   (479.25 MHz): no station
23   (487.25 MHz): no station
24   (495.25 MHz): no station
25   (503.25 MHz): no station
26   (511.25 MHz): no station
27   (519.25 MHz): no station
28   (527.25 MHz): no station
29   (535.25 MHz): no station
30   (543.25 MHz): no station
31   (551.25 MHz): no station
32   (559.25 MHz): no station
33   (567.25 MHz): no station
34   (575.25 MHz): no station
35   (583.25 MHz): no station
36   (591.25 MHz): no station
37   (599.25 MHz): no station
38   (607.25 MHz): no station
39   (615.25 MHz): no station
40   (623.25 MHz): no station
41   (631.25 MHz): no station
42   (639.25 MHz): no station
43   (647.25 MHz): no station
44   (655.25 MHz): no station
45   (663.25 MHz): no station
46   (671.25 MHz): no station
47   (679.25 MHz): no station
48   (687.25 MHz): no station
49   (695.25 MHz): no station
50   (703.25 MHz): no station
51   (711.25 MHz): no station
52   (719.25 MHz): no station
53   (727.25 MHz): no station
54   (735.25 MHz): no station
55   (743.25 MHz): no station
56   (751.25 MHz): no station
57   (759.25 MHz): no station
58   (767.25 MHz): no station
59   (775.25 MHz): no station
60   (783.25 MHz): no station
61   (791.25 MHz): no station
62   (799.25 MHz): no station
63   (807.25 MHz): no station
64   (815.25 MHz): no station
65   (823.25 MHz): no station
66   (831.25 MHz): no station
67   (839.25 MHz): no station
68   (847.25 MHz): no station
69   (855.25 MHz): no station
```



i check that into /etc/modules, /etc/modprobe.d/aliases and /etc/modprobe.d/option there aren't link to saa7134...

the strange things is that i try to work the card with a cd live dapper...and:



```
ubuntu@ubuntu:~$ sudo modprobe saa7134 card=59 tuner=54
ubuntu@ubuntu:~$ dmesg | grep saa
[4294728.686000] saa7130/34: v4l2 driver version 0.2.14 loaded
[4294728.686000] saa7133[0]: found at 0000:02:0a.0, rev: 208, irq: 217, latency:  32, mmio: 0xf6026000
[4294728.686000] saa7133[0]: subsystem: 1131:0000, board: UNKNOWN/GENERIC [card= 0,autodetected]
[4294728.686000] saa7133[0]: board init: gpio is 40
[4294728.787000] saa7133[0]: Huh, no eeprom present (err=-5)?
[4294728.787000] saa7133[0]: registered device video0 [v4l2]
[4294728.787000] saa7133[0]: registered device vbi0
[4294729.157000] saa7134 ALSA driver for DMA sound loaded
[4294729.157000] saa7133[0]/alsa: saa7133[0] at 0xf6026000 irq 217 registered as  card -1
[4295022.252000] saa7134 ALSA driver for DMA sound unloaded
[4295034.751000] saa7130/34: v4l2 driver version 0.2.14 loaded
[4295034.755000] saa7133[0]: found at 0000:02:0a.0, rev: 208, irq: 217, latency:  32, mmio: 0xf6026000
[4295034.755000] saa7133[0]: subsystem: 1131:0000, board: Kworld/Tevion V-Stream  Xpert TV PVR7134 [card=59,insmod option]
[4295034.755000] saa7133[0]: board init: gpio is 40
[4295034.807000] input: saa7134 IR (Kworld/Tevion V-Str as /class/input/input4
[4295034.997000] saa7133[0]: Huh, no eeprom present (err=-5)?
[4295035.034000] tuner 2-004b: chip found @ 0x96 (saa7133[0])
[4295035.121000] saa7133[0]: registered device video0 [v4l2]
[4295035.122000] saa7133[0]: registered device vbi0
[4295035.123000] saa7133[0]: registered device radio0
[4295035.142000] saa7134 ALSA driver for DMA sound loaded
[4295035.143000] saa7133[0]/alsa: saa7133[0] at 0xf6026000 irq 217 registered as  card -1
ubuntu@ubuntu:~$ tvtime-scanner
Reading configuration from /etc/tvtime/tvtime.xml
Scanning using TV standard PAL.
Scanning from  44.00 MHz to 958.00 MHz.
Checking  46.75 MHz:  - No signal
ubuntu@ubuntu:~$ sudo apt-get install scantv
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libzvbi-common libzvbi0 xawtv-plugins
The following NEW packages will be installed:
  libzvbi-common libzvbi0 scantv xawtv-plugins
0 upgraded, 4 newly installed, 0 to remove and 107 not upgraded.
Need to get 381kB of archives.
After unpacking 1348kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://archive.ubuntu.com dapper/universe libzvbi-common 0.2.17-5 [40.7kB]
Get:2 http://archive.ubuntu.com dapper/universe libzvbi0 0.2.17-5 [213kB]
Get:3 http://archive.ubuntu.com dapper/universe xawtv-plugins 3.94-1.0ubuntu2 [7 7.8kB]
Get:4 http://archive.ubuntu.com dapper/universe scantv 3.94-1.0ubuntu2 [49.5kB]
Fetched 381kB in 1s (333kB/s)
Selecting previously deselected package libzvbi-common.
(Reading database ... 75931 files and directories currently installed.)
Unpacking libzvbi-common (from .../libzvbi-common_0.2.17-5_all.deb) ...
Selecting previously deselected package libzvbi0.
Unpacking libzvbi0 (from .../libzvbi0_0.2.17-5_i386.deb) ...
Selecting previously deselected package xawtv-plugins.
Unpacking xawtv-plugins (from .../xawtv-plugins_3.94-1.0ubuntu2_i386.deb) ...
Selecting previously deselected package scantv.
Unpacking scantv (from .../scantv_3.94-1.0ubuntu2_i386.deb) ...
Setting up libzvbi-common (0.2.17-5) ...
Setting up libzvbi0 (0.2.17-5) ...

Setting up xawtv-plugins (3.94-1.0ubuntu2) ...
Setting up scantv (3.94-1.0ubuntu2) ...
ubuntu@ubuntu:~$ sudo scantv

please select your TV norm
   0: PAL
   1: PAL-BG
   2: PAL-I
   3: PAL-DK
   4: NTSC
   5: SECAM
   6: PAL-M
   7: PAL-Nc
   8: PAL-60
nr ? 1

please select a frequency table
   0: us-bcast
   1: us-cable
   2: us-cable-hrc
   3: japan-bcast
   4: japan-cable
   5: europe-west
   6: europe-east
   7: italy
   8: newzealand
   9: australia
  10: ireland
  11: france
  12: china-bcast
  13: southafrica
  14: argentina
  15: australia-optus
  16: russia
nr ? 7
[global]
freqtab = italy

[defaults]
input = Television
norm = PAL-BG


scanning channel list italy...
A    ( 53.75 MHz): no station
B    ( 62.25 MHz): no station
C    ( 82.25 MHz): no station
D    (175.25 MHz): RAI 1
[RAI 1]
channel = D

E    (183.75 MHz): no station
F    (192.25 MHz): no station
G    (201.25 MHz): no station
H    (210.25 MHz): no station
H1   (217.25 MHz): no station
H2   (224.25 MHz): no station
21   (471.25 MHz): no station
22   (479.25 MHz): Telecentro
[Telecentro]
channel = 22

23   (487.25 MHz): no station
24   (495.25 MHz): no station
25   (503.25 MHz): no station
26   (511.25 MHz): no station
27   (519.25 MHz): ???
[unknown (27)]
channel = 27

28   (527.25 MHz): RAI 2
[RAI 2]
channel = 28

29   (535.25 MHz): ???
[unknown (29)]
channel = 29

30   (543.25 MHz): LA7
[LA7]
channel = 30

31   (551.25 MHz): no station
32   (559.25 MHz): no station
33   (567.25 MHz): ???
[unknown (33)]
channel = 33

34   (575.25 MHz): ???
[unknown (34)]
channel = 34

35   (583.25 MHz): ???
[unknown (35)]
channel = 35

36   (591.25 MHz): no station
37   (599.25 MHz): no station
38   (607.25 MHz): no station
39   (615.25 MHz): no station
40   (623.25 MHz): no station
41   (631.25 MHz): no station
42   (639.25 MHz): ???
[unknown (42)]
channel = 42

43   (647.25 MHz): ???
[unknown (43)]
channel = 43

44   (655.25 MHz): Telesanterno
[Telesanterno]
channel = 44

45   (663.25 MHz): no station
46   (671.25 MHz): no station
47   (679.25 MHz): no station
48   (687.25 MHz): RAI 3
[RAI 3]
channel = 48

49   (695.25 MHz): no station
50   (703.25 MHz): no station
51   (711.25 MHz): MTV Italia
[MTV Italia]
channel = 51

52   (719.25 MHz): no station
53   (727.25 MHz): no station
54   (735.25 MHz): Rete 4
[Rete 4]
channel = 54

55   (743.25 MHz): ???
[unknown (55)]
channel = 55

56   (751.25 MHz): no station
57   (759.25 MHz): Italia 1
[Italia 1]
channel = 57

58   (767.25 MHz): no station
59   (775.25 MHz): Canale 5
[Canale 5]
channel = 59

60   (783.25 MHz): no station
61   (791.25 MHz): no station
62   (799.25 MHz): no station
63   (807.25 MHz): no station
64   (815.25 MHz): no station
65   (823.25 MHz): no station
66   (831.25 MHz): ???
[unknown (66)]
channel = 66

67   (839.25 MHz): no station
68   (847.25 MHz): no station
69   (855.25 MHz): no station
ubuntu@ubuntu:~$ sudo tvtime
Running tvtime 1.0.1.
Reading configuration from /etc/tvtime/tvtime.xml
I/O warning : failed to load external entity "/home/ubuntu/.tvtime/tvtime.xml"
I/O warning : failed to load external entity "/home/ubuntu/.tvtime/stationlist.x ml"
station: No station file found, creating a new one.
Thank you for using tvtime.
```

i watched tv!!!
so why with edgy on the disk don't work and with dapper live work? is there a kernel problem?

Daniele...

---

### Post by crispy_420 on 2007-04-06
You may have to tell the OS to load the module in /etc/modules. I have a bttv based card so I don't have the know how to get specific but hopefully this points you in the right direction. But basically you need to tell the kernel to load the saa driver.

---

