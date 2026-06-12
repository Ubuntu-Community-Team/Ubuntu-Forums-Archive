---
title: "Dvico FusionHDTV Express problems"
date: 2008-04-07
forum: Multimedia &amp; Video
---

### Post by Dionikon on 2008-04-07
Hey there, I posted this in the noob forum but wasn't getting any luck with replies.  So I figured I'd put a pointer here because it's a more relevant section.

[http://ubuntuforums.org/showthread.php?t=746783](http://ubuntuforums.org/showthread.php?t=746783)

I'm completely stuck trying to get my Dvico card to work.  It shows up in dmesg but is not working correctly.  This is what dmesg returns:

```

[   30.780310] cx23885 driver version 0.0.1 loaded
[   30.780681] cx23885[0]: Your board isn't known (yet) to the driver.  You can
[   30.780682] cx23885[0]: try to pick one of the existing card configs via
[   30.780684] cx23885[0]: card=<n> insmod option.  Updating to the latest
[   30.780685] cx23885[0]: version might help as well.
[   30.780687] cx23885[0]: Here is a list of valid choices for the card=<n> insmod option:
[   30.780688] cx23885[0]:    card=0 -> UNKNOWN/GENERIC
[   30.780690] cx23885[0]:    card=1 -> Hauppauge WinTV-HVR1800lp
[   30.780692] cx23885[0]:    card=2 -> Hauppauge WinTV-HVR1800
[   30.780693] cx23885[0]:    card=3 -> Hauppauge WinTV-HVR1250
[   30.780695] cx23885[0]:    card=4 -> DViCO FusionHDTV5 Express
[   30.780697] cx23885[0]:    card=5 -> Hauppauge WinTV-HVR1500Q
[   30.780698] cx23885[0]:    card=6 -> Hauppauge WinTV-HVR1500
[   30.780705] CORE cx23885[0]: subsystem: 18ac:db30, board: UNKNOWN/GENERIC [card=0,autodetected]
[   30.887552] cx23885[0]: i2c bus 0 registered
[   30.887600] cx23885[0]: i2c bus 1 registered
[   30.887628] cx23885[0]: i2c bus 2 registered
[   30.914304] cx23885_dev_checkrevision() Hardware revision = 0xb0
[   30.914312] cx23885[0]/0: found at 0000:03:00.0, rev: 2, irq: 16, latency: 0, mmio: 0xe5000000


```

Appreciate any help you guys can give.

Cheers

Nathan

---

### Post by warp99 on 2008-04-08
Here is the answer to you question if your using Gusty 7.10 or below:

[http://ubuntuforums.org/showpost.php?p=3517683&postcount=4](http://ubuntuforums.org/showpost.php?p=3517683&postcount=4)

You have to compile the the driver from source, install, and then add the following to your /etc/modprobe.d/options file:

options cx23885 card=4

Now if your using Hardy 8.04 you only need to add the line to your options file since the module is already included with the kernel packages.

[http://packages.ubuntu.com/search?suite=hardy&arch=i386&mode=exactfilename&searchon=contents&keywords=cx23885.ko](http://packages.ubuntu.com/search?suite=hardy&arch=i386&mode=exactfilename&searchon=contents&keywords=cx23885.ko)

Edit:

You can also add the string to the options file with this command:
```
echo "options cx23885 card=4" | sudo tee -a /etc/modprobe.d/options
```

---

### Post by Dionikon on 2008-04-08
So it was as simple as that then?

Thanks!

dmesg shows this now:

```

[   31.723567] cx23885 driver version 0.0.1 loaded
[   31.723931] CORE cx23885[0]: subsystem: 18ac:db30, board: DViCO FusionHDTV5 Express [card=4,insmod option]
[   31.824046] cx23885[0]: i2c bus 0 registered
[   31.824064] cx23885[0]: i2c bus 1 registered
[   31.824078] cx23885[0]: i2c bus 2 registered
[   31.850727] cx23885[0]: cx23885 based dvb card
[   31.886308] DVB: registering new adapter (cx23885[0])
[   31.886519] cx23885_dev_checkrevision() Hardware revision = 0xb0
[   31.886526] cx23885[0]/0: found at 0000:03:00.0, rev: 2, irq: 16, latency: 0, mmio: 0xe5000000

```

So it looks like it should work now.

However, when I try to scan for channels in MythTV I can't find any at all.  If I run this:
```
tail -f /var/log/messages 
```
I see these messages while trying to tune:
```
Apr  8 20:38:13 MYTH-STERISK kernel: [ 2790.790602] DVB: frontend 0 frequency 887000000 out of range (54000000..858000000
```

It looks like I may have a MythTV problem now.  Although getting the tv card to work with kaffeine doesn't seem to work either.

I'm off to do some testing now.  [http://www.linuxtv.org/wiki/index.php/Testing_your_DVB_device](http://www.linuxtv.org/wiki/index.php/Testing_your_DVB_device)

Thanks again Warp99!  I was almost at the point of giving up and installing that other OS that I wont mention here for fear of being banned. :p  

(just kidding, nothing could be that bad)  :lolflag:

---

### Post by Dionikon on 2008-04-08
Hmm... just when I thought I was making some progress.

Attempting to run a scan fails for some reason, I can't figure it out.

I run this command:
```
sudo scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/au-Melbourne[/quote]

According to this page the scan should take a while, it doesn't, the scan finishes in less than 1 second.

http://www.linuxtv.org/wiki/index.php/Testing_your_DVB_device

The return I get is:
[code]
scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/au-Melbourne
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 226500000 1 3 9 3 1 1 0
initial transponder 177500000 1 2 9 3 1 2 0
initial transponder 191625000 1 3 9 3 1 1 0
initial transponder 219500000 1 3 9 3 1 1 0
initial transponder 536625000 1 2 9 3 1 2 0
WARNING: frontend type (ATSC) is not compatible with requested tuning type (OFDM)
WARNING: frontend type (ATSC) is not compatible with requested tuning type (OFDM)
WARNING: frontend type (ATSC) is not compatible with requested tuning type (OFDM)
WARNING: frontend type (ATSC) is not compatible with requested tuning type (OFDM)
WARNING: frontend type (ATSC) is not compatible with requested tuning type (OFDM)
ERROR: initial tuning failed
dumping lists (0 services)
Done.

```

Once again, I don't know where to look for this, google seems to have abandoned me in my time of need. ;)

I suspect there is something not quite right with the way I have loaded the drivers.  In my research so far I have read that a lspci command should list a Fusion Device.  This is not the case with my system, I see this:

```

00:00.0 Host bridge: nVidia Corporation Unknown device 07c1 (rev a2)
00:00.1 RAM memory: nVidia Corporation Unknown device 07cb (rev a2)
00:01.0 RAM memory: nVidia Corporation Unknown device 07cd (rev a1)
00:01.1 RAM memory: nVidia Corporation Unknown device 07ce (rev a1)
00:01.2 RAM memory: nVidia Corporation Unknown device 07cf (rev a1)
00:01.3 RAM memory: nVidia Corporation Unknown device 07d0 (rev a1)
00:01.4 RAM memory: nVidia Corporation Unknown device 07d1 (rev a1)
00:01.5 RAM memory: nVidia Corporation Unknown device 07d2 (rev a1)
00:01.6 RAM memory: nVidia Corporation Unknown device 07d3 (rev a1)
00:02.0 RAM memory: nVidia Corporation Unknown device 07d6 (rev a1)
00:03.0 ISA bridge: nVidia Corporation Unknown device 07d7 (rev a2)
00:03.1 SMBus: nVidia Corporation Unknown device 07d8 (rev a1)
00:03.2 RAM memory: nVidia Corporation Unknown device 07d9 (rev a1)
00:03.4 RAM memory: nVidia Corporation Unknown device 07c8 (rev a1)
00:04.0 USB Controller: nVidia Corporation Unknown device 07fe (rev a1)
00:04.1 USB Controller: nVidia Corporation Unknown device 056a (rev a1)
00:08.0 IDE interface: nVidia Corporation Unknown device 056c (rev a1)
00:09.0 Audio device: nVidia Corporation Unknown device 07fc (rev a1)
00:0a.0 PCI bridge: nVidia Corporation Unknown device 056d (rev a1)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 056e (rev a1)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 056f (rev a1)
00:0d.0 PCI bridge: nVidia Corporation Unknown device 056f (rev a1)
00:0e.0 SATA controller: nVidia Corporation Unknown device 07f4 (rev a2)
00:0f.0 Ethernet controller: nVidia Corporation Unknown device 07dc (rev a2)
01:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
02:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7300 GT] (rev a1)
03:00.0 Multimedia video controller: Conexant Unknown device 8852 (rev 02)

```

I might be wrong but it seems that there are a lot of drivers in my system that are not detecting correctly.  

lspci -vv shows: 
```

03:00.0 Multimedia video controller: Conexant Unknown device 8852 (rev 02)
        Subsystem: DViCO Corporation Unknown device db30
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at e5000000 (64-bit, non-prefetchable) [size=2M]
        Capabilities: <access denied>

```

Seems strange to me, I'm thinking a rebuild may be required so that I can start from a clean slate again.

I'll stop typing now, I'm running out of code/log snippets to copy and paste.
:p

---

