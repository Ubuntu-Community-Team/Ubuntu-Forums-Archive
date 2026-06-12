---
title: "Trouble with ATSC signals in 9.10 using a PCTV HD 800i"
date: 2010-04-28
forum: Mythbuntu
---

### Post by Zachs Kappler on 2010-04-28
This card is driving me nuts! Linux sees it, MythTv sees it, and TVTime can use the NTSC, Composite, and S-Video connections, but it refuses to pick up or use ATSC channels. Anybody have this straightened out or will I be getting another tuner?

I attached the spec sheet Sysinfo put out just in case you might need it

Also before I forget a output of connected devices:
```

00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 12)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 12)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 12)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
02:07.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
02:07.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
02:07.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
02:08.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)
02:09.0 Network controller: RaLink RT2561/RT61 802.11g PCI
02:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

---

### Post by J.H. on 2010-04-28
I have the same issue as well. Just got the card last week, and I can't get it to find any ATSC channels either. ](*,)

---

### Post by Zachs Kappler on 2010-05-15
I just did a fresh install of Mythbuntu 10.04 and I still have this problem, but now it mocks me. A command-line only channel scanning tool I installed from the repos called w-scan can apparently utilize the tuner and identify all the channels, but no matter what I do, it refuses to write down it's findings in a file mythtv or tvtime can read!


Edit: I got the latest build of w-scan from the creator's website and after using a few switches in it, I got a rather detailed sheet about the channels it found, but failed to still make a file.

```

KTHV-DT;(null):207000:M10:A:0:49:52=eng,53=spa:0:0:1:0:0:0
THV2;(null):207000:M10:A:0:65:68=eng:0:0:2:0:0:0
KATV-HD;(null):521000:M10:A:0:49:52=eng:0:0:3:0:0:0
RTV;(null):521000:M10:A:0:65:68=eng:0:0:4:0:0:0
AccuWX;(null):521000:M10:A:0:81:84=eng:0:0:5:0:0:0
KLRT DT;(null):569000:M10:A:0:49:52=eng:0:0:3:0:0:0
KLRT DT-2;(null):569000:M10:A:0:65:68=eng:0:0:4:0:0:0
KARK-DT;(null):581000:M10:A:0:49:52=eng:0:0:3:0:0:0
KKAP-DT;(null):605000:M10:A:0:49:52=eng:0:0:3:0:0:0
KASN Pine Bluff, AR;(null):623000:M10:A:0:49:52=eng:0:0:3:0:0:0
KARZ-DT;(null):653000:M10:A:0:49:52=eng:0:0:3:0:0:0

```

w-scan also lies about lacking ATSC support when this string made it find ATSC channels:
```

./w_scan -c US -f A1 -o 7

```

Any ideas on how to translate what it spat out into something I can use? the link for example channel lists on his site was broken.

---

### Post by wirbel2 on 2010-05-16
You did several mistakes at once.

tell the program to use a ATSC frontend:
**-fa**

and then you have to choose the output format your program can read, you choose "-o 7", that means "create a output for VDR version 1.7". VDR is *not* mythtv, see [http://www.tvdr.de/](http://www.tvdr.de/).
Since you want to use mythtv, you need to choose a channel format mythtv can read, not the VDR channel format. Most probably the "-X" switch (uppercase!) will work.

And the last thing is, that you need to use file io redirection to write the text into a file.

Pls try for aerial..

w_scan -fa -A1 -cUS -X > ~/channels.conf

or for digital cable..

w_scan -fa -A2 -cUS -X > ~/channels.conf

After that you should find a channels.conf in your home directory.

---

