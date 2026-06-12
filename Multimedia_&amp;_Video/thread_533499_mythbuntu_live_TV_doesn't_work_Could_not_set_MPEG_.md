---
title: "mythbuntu: live TV doesn't work: Could not set MPEG controls"
date: 2007-08-24
forum: Multimedia &amp; Video
---

### Post by tedder on 2007-08-24
I'm using a new install of MythBuntu (with a Hauppage *50 card, not the 350). When I try to watch live TV, I get the following: 

2007-08-23 22:13:15.837 MainServer::HandleAnnounce Playback
2007-08-23 22:13:15.839 adding: mythtv1 as a client (events: 0)
2007-08-23 22:13:15.843 TVRec(1): Changing from None to WatchingLiveTV
2007-08-23 22:13:15.847 TVRec(1): HW Tuner: 1->1
2007-08-23 22:13:15.992 MPEGRec(/dev/video0) Error: Could not set MPEG controls
                        eno: Invalid argument (22)
2007-08-23 22:14:02.508 TVRec(1): Changing from WatchingLiveTV to None
2007-08-23 22:14:02.519 Finished recording Boston Legal "Son of the Defender": channel 2129

You'll note the long timeout (45 seconds). It just displays a blank/black screen during that time.

I ran "chmod a+w" on /dev/video0, it looks like this now:
crw-rw-rw- 1 root video 81, 0 2007-08-23 21:41 /dev/video0

I still get the same error. How can I figure what "control" it is trying to set? Googling ([1](http://www.google.com/search?q=mythtv+%22blank+screen%22&btnG=google), [2](http://www.google.com/search?q=mythtv+%22Could+not+set+MPEG+controls%22&btnG=google)) didn't help much besides the permissions issue, though I'm new with mythtv so I may not know the magic keywords.

Solution? Ideas? Shot in the dark?


Now for relevant configuration- here are some lines from dmesg:
```

[   13.024000] Linux video capture interface: v2.00
[   13.160000] bttv: driver version 0.9.17 loaded
[   13.160000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   13.160000] bttv: Bt8xx card found (0).
[   13.160000] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 16 (level, low) -> IRQ
 19
[   13.160000] bttv0: Bt878 (rev 17) at 0000:00:09.0, irq: 19, latency: 32, mmio
: 0xea000000
[   13.160000] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0
070:13eb
[   13.160000] bttv0: using: Hauppauge (bt878) [card=10,autodetected]
[   13.160000] bttv0: gpio: en=00000000, out=00000000 in=00ffffdb [init]
[   13.160000] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
[   13.188000] tveeprom 0-0050: Hauppauge model 44811, rev D123, serial# 6131127
[   13.188000] tveeprom 0-0050: tuner model is Philips FM1236 (idx 23, type 2)
[   13.188000] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[   13.188000] tveeprom 0-0050: audio processor is None (idx 0)
[   13.188000] tveeprom 0-0050: has radio
[   13.188000] bttv0: Hauppauge eeprom indicates model#44811
[   13.188000] bttv0: using tuner=2
[   13.188000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   13.756000] bttv0: i2c: checking for TDA9875 @ 0xb0... <6>NET: Registered protocol family 17
[   13.848000] not found
[   13.848000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   14.288000] input: PC Speaker as /class/input/input4
[   14.680000] parport_pc 00:09: reported by Plug and Play ACPI
[   14.680000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   14.756000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[   14.880000] tuner 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[   14.880000] tuner 0-0061: type set to 2 (Philips NTSC (FI1236,FM1236 and compatibles))
[   14.880000] tuner 0-0061: type set to 2 (Philips NTSC (FI1236,FM1236 and compatibles))
[   14.888000] bttv0: registered device video0
[   14.888000] bttv0: registered device vbi0
[   14.888000] bttv0: registered device radio0
[   14.888000] bttv0: PLL: 28636363 => 35468950 .. ok

```

output of lspci:
```

00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
00:09.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
00:09.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: 3Dfx Interactive, Inc. Voodoo 3 (rev 01)

```

finally, scanpci:
```


pci bus 0x0000 cardnum 0x00 function 0x00: vendor 0x1106 device 0x3099
 VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]

pci bus 0x0000 cardnum 0x01 function 0x00: vendor 0x1106 device 0xb099
 VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]

pci bus 0x0000 cardnum 0x09 function 0x00: vendor 0x109e device 0x036e
 Brooktree Corporation Bt878 Video Capture

pci bus 0x0000 cardnum 0x09 function 0x01: vendor 0x109e device 0x0878
 Brooktree Corporation Bt878 Audio Capture

pci bus 0x0000 cardnum 0x10 function 0x00: vendor 0x1106 device 0x3038
 VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller

pci bus 0x0000 cardnum 0x10 function 0x01: vendor 0x1106 device 0x3038
 VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller

pci bus 0x0000 cardnum 0x10 function 0x02: vendor 0x1106 device 0x3038
 VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller

pci bus 0x0000 cardnum 0x10 function 0x03: vendor 0x1106 device 0x3104
 VIA Technologies, Inc. USB 2.0

pci bus 0x0000 cardnum 0x11 function 0x00: vendor 0x1106 device 0x3177
 VIA Technologies, Inc. VT8235 ISA Bridge

pci bus 0x0000 cardnum 0x11 function 0x01: vendor 0x1106 device 0x0571
 VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE

pci bus 0x0000 cardnum 0x11 function 0x05: vendor 0x1106 device 0x3059
 VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller

pci bus 0x0000 cardnum 0x12 function 0x00: vendor 0x1106 device 0x3065
 VIA Technologies, Inc. VT6102 [Rhine-II]

pci bus 0x0001 cardnum 0x00 function 0x00: vendor 0x121a device 0x0005
 3Dfx Interactive, Inc. Voodoo 3

```

Also, I tried "cat /dev/video0 > test.mpg", then playing it in Windows (sorry), but it complained about not supporting the file type (because of not having headers, perhaps?).

hexdump of test.mpg:
```

# hexdump test.mpg | head
0000000 ffff ffff ffff ffff ffff ffff ffff ffff
*
0000b40 fffe feff ffff ffff ffff ffff ffff ffff
0000b50 ffff ffff ffff ffff ffff ffff ffff ffff
*
00032a0 fff8 fcff ffff ffff ffff ffff ffff ffff
00032b0 ffff ffff ffff ffff ffff ffff ffff ffff
*
0003820 ffff ffff ffff ffff fffc fcff ffff fffe
0003830 ffff ffff ffff ffff ffff ffff ffff ffff

```

Finally, I get display when I run 'motv'.

---

