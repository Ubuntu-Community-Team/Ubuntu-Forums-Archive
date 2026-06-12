---
title: "Driver installation WinTV PVR USB2"
date: 2007-04-21
forum: Multimedia &amp; Video
---

### Post by Temis on 2007-04-21
Hi, did anybody successfully install driver for Win TV PVR Usb2 on Feisty. I downloaded the driver and script from here    [http://www.isely.net/pvrusb2.html](http://www.isely.net/pvrusb2.html)     but have no clue how  to go about it.

---

### Post by Temis on 2007-04-22
Well I'll wait,    maybe the next kernel upgrade won't require or will include the script.

---

### Post by dogatemycomputer on 2007-06-21
> **Temis said:**
> Hi, did anybody successfully install driver for Win TV PVR Usb2 on Feisty. I downloaded the driver and script from here    [http://www.isely.net/pvrusb2.html](http://www.isely.net/pvrusb2.html)     but have no clue how  to go about it.

I was able to get wintv-pvr-usb2 working on Feisty.  I was only interested in watching channel 4 because its connected to my Tivo so I use mplayer.  If this process works then configuring mythtv should be pretty easy.  I tested it with mythtv and it does work although you'll need to mess around with the configuration options to get it to work properly.

I should also note that this writeup assumes you're watching channel 4 using live TV.  Once you get this functionality working then do a google search for mplayer and mencoder.  There are ways of dumping the video stream directly to your hard disk then piping it through mplayer so you can pause/rewind/fast-forward live streams, edit the resulting files, burn the contents to DVD or put them on a portable hard disk for future viewing/editing.    

I'm a noob AND its 2am here so i'm really exhausted.  I wanted to do this writeup while it was fresh in my head.  If you see something mistyped or a better way of doing something then PLEASE email me at [email]dogatemycomputer@gmail.com[/email] so I can amend the post.  Of course, you can always post a follow-up article also but i find it easier to fix the original work. 

I'm running:

```
walkerd@linux:~$ uname -r
2.6.20-16-generic
```

```
walkerd@linux:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.04
Release:        7.04
Codename:       feisty
```

My PC is a standard Dell Optiplex 745.

```
walkerd@linux:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300/X1550 Series
OpenGL version string: 2.0.6334 (8.34.8)
```

Once you connect the wintv-pvr-usb2 then:

```
dmesg | tail -n 50 | more
```

Which should return something that looks like this:

```
walkerd@linux:~$ dmesg | tail -n 50 | more
[   30.927704] tg3.c:v3.72 (January 8, 2007)
[   30.927726] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   30.927961] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   30.955256] eth0: Tigon3 [partno(BCM95754) rev b002 PHY(5787)] (PCI Express) 10/100/1000Base-T Ethernet 00:18:8b:56:a3:da
[   30.955263] eth0: RXcsums[1] LinkChgREG[1] MIirq[1] ASF[0] Split[0] WireSpeed[1] TSOcap[1]
[   30.955266] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   35.080032] tg3: eth0: Link is up at 1000 Mbps, full duplex.
[   35.080037] tg3: eth0: Flow control is on for TX and on for RX.
[  240.157902] usb 3-1: USB disconnect, address 5
[  240.158423] drivers/usb/class/usblp.c: usblp0: removed
[  246.055713] usb 3-2: new full speed USB device using uhci_hcd and address 6
[  246.241483] usb 3-2: configuration #1 chosen from 1 choice
[  246.249419] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 6 if 0 alt 0 proto 2 vid 0x043D pid 0x0052
[  285.316123] usb 3-2: USB disconnect, address 6
[  285.316186] drivers/usb/class/usblp.c: usblp0: removed
[  296.668535] usb 1-4: new high speed USB device using ehci_hcd and address 13
[  296.801575] usb 1-4: configuration #1 chosen from 1 choice
[  296.916636] usb 1-4: reset high speed USB device using ehci_hcd and address 13
[  297.452874] msp3400 0-0040: MSP3445G-B8 found @ 0x80 (pvrusb2_a)
[  297.452878] msp3400 0-0040: MSP3445G-B8 supports radio, mode is autodetect and autoselect
[  297.515643] saa7115 0-0021: saa7115 found (1f7115d0e100000) @ 0x42 (pvrusb2_a)
[  297.726152] tuner 0-0043: chip found @ 0x86 (pvrusb2_a)
[  297.726187] tda9887 0-0043: tda988[5/6/7] found @ 0x43 (tuner)
[  297.761093] tuner 0-0061: chip found @ 0xc2 (pvrusb2_a)
[  297.791294] tveeprom 0-0050: Hauppauge model 29032, rev D1A3, serial# 8013975
[  297.791299] tveeprom 0-0050: tuner model is TCL MFNM05-4 (idx 103, type 43)
[  297.791301] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[  297.791304] tveeprom 0-0050: audio processor is MSP3445 (idx 12)
[  297.791306] tveeprom 0-0050: decoder processor is SAA7115 (idx 19)
[  297.791308] tveeprom 0-0050: has radio, has IR receiver, has no IR transmitter
[  297.820620] tuner 0-0061: type set to 43 (Philips NTSC MK3 (FM1236MK3 or FM1236/F))
[  298.005670] msp3400 0-0040: MSP3445G-B8 rev1 = 0x0207 rev2 = 0x2d48
[  298.005675] msp3400 0-0040: Audio:    volume 65535
[  298.005677] msp3400 0-0040: Audio:    balance 0 bass 0 treble 0 loudness off
[  298.005680] msp3400 0-0040: Standard: autodetect start (mono)
[  298.005682] msp3400 0-0040: Audmode:  0x0001
[  298.005684] msp3400 0-0040: Routing:  0x00000000 (input) 0x00000044 (output)
[  298.005686] msp3400 0-0040: ACB:      0x0c00
[  298.005688] saa7115 0-0021: Audio frequency: 48000 Hz
[  298.007416] saa7115 0-0021: Input:           Composite 4
[  298.007419] saa7115 0-0021: Video signal:    bad
[  298.007420] saa7115 0-0021: Frequency:       60 Hz
[  298.007422] saa7115 0-0021: Detected format: BW/No color
[  298.007424] saa7115 0-0021: Width, Height:   720, 480
[  298.007427] tda9887 0-0043: Data bytes: b=0x14 c=0x30 e=0x44
[  298.007429] tuner 0-0061: Tuner mode:      analog TV
[  298.007431] tuner 0-0061: Frequency:       175.25 MHz
[  298.007433] tuner 0-0061: Standard:        0x00000100
[  298.007437] pvrusb2: Device initialization completed successfully.
[  298.007462] pvrusb2: registered device **video0** [mpeg]
walkerd@linux:~$   

```

Notice, in bold, that it registers the device as **video0**.  It really means the stream is being piped to:

```
/dev/video0 
```

If dmesg doesn't return something similar to what you see above then make sure the correct kernel module is loaded:

```
sudo lsmod | grep -i pvr
```

should return something like this:

```
walkerd@linux:~$ lsmod | grep -i pvr
pvrusb2               139220  0
cx2341x                12804  1 pvrusb2
videodev               28160  1 pvrusb2
v4l2_common            25216  6 tuner,saa7115,msp3400,pvrusb2,cx2341x,videodev
v4l1_compat            15236  2 pvrusb2,videodev
tveeprom               15888  1 pvrusb2
i2c_core               22656  6 i2c_ec,tuner,saa7115,msp3400,pvrusb2,tveeprom
usbcore               134280  8 ipaq,usbserial,usblp,pvrusb2,usbhid,uhci_hcd,ehci_hcd
```


If not then:

```
modprobe pvrusb2
depmod -a
```


Then repeat.  If the module does not load on its own then try updating your installation:

```

sudo apt-get update
sudo apt-get upgrade
```

Check your power and usb cables to make sure they're all plugged in and there are no other obvious issues.

If you want to test your device with mplayer then:

```
sudo apt-get install mplayer w32codecs libdvdcss mplayer-doc ladspa-sdk
```

For some reason that I can't explain..  Once I do the basic installation I usually get nothing but a blank box (mplayer won't be able to load), static or something else other than video.    
                                              
If I do this:

```
sudo apt-get install mythtv mythtv-database mysql-server mysql-server-5.0 mythtv-frontend mythtv-backend mythtv-common mythtv-common mysql-client mysql-client-5.0
```

then this:

```
mplayer -framedrop -tv channel=4 /dev/video0
```

It plays fine.  

I have modified my system a few times so i'm not sure if you need some special codecs or something for mplayer to decode the mpeg2 stream.  Hopefully someone won't mind doing a fresh installation then commenting on any missing steps. 
[B]
I should also note that putting your machine to sleep (hibernation or standby), unplugging/reconnecting the PVR or even shutting down/rebooting your machine may cause the device to stop responding.  This is the solution I have found that works for me.  Hopefully you can adapt it to fit your needs:[/B]

I have found this line of code that completely removes mysql and mythtv:
```

sudo apt-get remove mythtv mythtv-database mysql-server mysql-server-5.0 mythtv-frontend mythtv-backend mythtv-common mythtv-common mysql-client mysql-client-5.0
```

followed by this line of code that reinstalls mysql and mythtv:

```
sudo apt-get install mythtv mythtv-database mysql-server mysql-server-5.0 mythtv-frontend mythtv-backend mythtv-common mythtv-common mysql-client mysql-client-5.0
```

Will usually resolve the problem.  I've gone so far as to write a shell script that I run whenever I wanna watch TV it automatically uninstalls then reinstalls mythtv and mysql without prompting then loads mplayer automatically and tunes it to channel 4:

```
sudo apt-get --assume-yes remove mythtv mythtv-database mysql-server mysql-server-5.0 mythtv-frontend mythtv-backend mythtv-common mythtv-common mysql-client mysql-client-5.0 && sleep 3 && sudo apt-get --assume-yes install mythtv mythtv-database mysql-server mysql-server-5.0 mythtv-frontend mythtv-backend mythtv-common mythtv-common mysql-client mysql-client-5.0
```
[B]
Please keep in mind the above scripts make automatic changes to your machine.  Sometimes removing one package can automatically remove several other packages that shouldn't be removed.  This kind of dependency hell can cause alot of problems if you aren't careful.  [/B]



If you want to know what channels you can get:

```
sudo apt-get install scantv
```

then 

```
$ scantv -C /dev/video0
```

Which should return something like this (this example assumes I get channel 4, 33, 45 and 51 on a standard NTSC-M using standard broadcast frequencies):

```

please select your TV norm
   0: PAL-M
   1: PAL-N
   2: PAL-Nc
   3: NTSC-M
   4: NTSC-Mj
   5: NTSC-Mk
nr ? 3

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
nr ? 0
[global]
freqtab = us-bcast

[defaults]
input = Television
norm = NTSC-M


scanning channel list us-bcast...
2    ( 55.25 MHz): no station
3    ( 61.25 MHz): no station
4    ( 67.25 MHz): ???
[unknown (4)]
channel = 4

5    ( 77.25 MHz): no station
6    ( 83.25 MHz): no station
7    (175.25 MHz): no station
8    (181.25 MHz): no station
9    (187.25 MHz): no station
10   (193.25 MHz): no station
11   (199.25 MHz): no station
12   (205.25 MHz): no station
13   (211.25 MHz): no station
14   (471.25 MHz): no station
15   (477.25 MHz): no station
16   (483.25 MHz): no station
17   (489.25 MHz): no station
18   (495.25 MHz): no station
19   (501.25 MHz): no station
20   (507.25 MHz): no station
21   (513.25 MHz): no station
22   (519.25 MHz): no station
23   (525.25 MHz): no station
24   (531.25 MHz): no station
25   (537.25 MHz): no station
26   (543.25 MHz): no station
27   (549.25 MHz): no station
28   (555.25 MHz): no station
29   (561.25 MHz): no station
30   (567.25 MHz): no station
31   (573.25 MHz): no station
32   (579.25 MHz): no station
33   (585.25 MHz): ???
[unknown (33)]
channel = 33

34   (591.25 MHz): no station
35   (597.25 MHz): no station
36   (603.25 MHz): no station
37   (609.25 MHz): no station
38   (615.25 MHz): no station
39   (621.25 MHz): no station
40   (627.25 MHz): no station
41   (633.25 MHz): no station
42   (639.25 MHz): no station
43   (645.25 MHz): no station
44   (651.25 MHz): no station
45   (657.25 MHz): ???
[unknown (45)]
channel = 45

46   (663.25 MHz): no station
47   (669.25 MHz): no station
48   (675.25 MHz): no station
49   (681.25 MHz): no station
50   (687.25 MHz): no station
51   (693.25 MHz): ???
[unknown (51)]
channel = 51

52   (699.25 MHz): no station
53   (705.25 MHz): no station
54   (711.25 MHz): no station
55   (717.25 MHz): no station
56   (723.25 MHz): no station
57   (729.25 MHz): no station
58   (735.25 MHz): no station
59   (741.25 MHz): no station
60   (747.25 MHz): no station
61   (753.25 MHz): no station
62   (759.25 MHz): no station
63   (765.25 MHz): no station
64   (771.25 MHz): no station
65   (777.25 MHz): no station
66   (783.25 MHz): no station
67   (789.25 MHz): no station
68   (795.25 MHz): no station
69   (801.25 MHz): no station
70   (807.25 MHz): no station
71   (813.25 MHz): no station
72   (819.25 MHz): no station
73   (825.25 MHz): no station
74   (831.25 MHz): no station
75   (837.25 MHz): no station
76   (843.25 MHz): no station
77   (849.25 MHz): no station
78   (855.25 MHz): no station
79   (861.25 MHz): no station
80   (867.25 MHz): no station
81   (873.25 MHz): no station
82   (879.25 MHz): no station
83   (885.25 MHz): no station
walkerd@linux:~$                                          


```

If video freezes up after several minutes or you can't get the video to display in full screen mode then its possible there is something wrong with X.  If you are running an OpenGL compliant video card and your display is configured properly (which is outside the scope of this tutorial) then you can try another video output option:

```
mplayer -framedrop -vo gl2 -tv channel=4 /dev/video0
```

I still don't understand:

- is there a simpler way to get picture back after a machine has been to hibernation or standby that doesn't require reinstalling mythtv?
- why do I need mythtv install for mplayer to function properly anyway?  is there a particular file/codec that i'm missing that would be easier to reinstall?  Uninstalling/reinstalling each of these packages seperately will not resolve the problem but uninstalling/reinstalling as a group does the trick.
- why can't I see the composite input video signal?  is there something I can do to make that visible in addition to channel 4?

Could someone else post to let us know if this process works on other Hauppauge cards and devices?  

If someone can recommend a fix for this then please post and email me at [email]dogatemycomputer@gmail.com[/email].  Thanks!

---

