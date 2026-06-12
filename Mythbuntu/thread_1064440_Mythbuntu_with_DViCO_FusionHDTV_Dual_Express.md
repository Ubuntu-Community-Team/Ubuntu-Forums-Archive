---
title: "Mythbuntu with DViCO FusionHDTV Dual Express"
date: 2009-02-08
forum: Mythbuntu
---

### Post by gavin0001 on 2009-02-08
Hi All,

I'm attempting to get Mythbuntu to use the FusionHDTV Express, however I'm having a few problems with it, despite going through the step-by-step guides that I've found. I've been messing around with it for a couple of months now and have had no luck. It might be a driver issue, could even be something as simple as an antenna issue (have not had an oppurtunity to test this though), but it refuses to receive any tv signals and it will not tune (I ended up download a config file for Brisbane). I have attached *dmesg | grep cx* and *lspci* outputs. If anything else is required, please let me know, as I'd really like to get this working.

Thanks in advance,

Gavin

dmesg:
[    8.655384] cx23885 driver version 0.0.1 loaded
[    8.655445] cx23885 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.655578] CORE cx23885[0]: subsystem: 18ac:db78, board: DViCO FusionHDTV DVB-T Dual Express [card=11,insmod option]
[    9.672235] ir-kbd-i2c: i2c IR (FusionHDTV) detected at i2c-0/0-006b/ir0 [cx23885[0]]
[    9.672659] cx23885_dvb_register() allocating 1 frontend(s)
[    9.672665] cx23885[0]: cx23885 based dvb card
[   10.004054] DVB: registering new adapter (cx23885[0])
[   10.004954] cx23885_dvb_register() allocating 1 frontend(s)
[   10.004962] cx23885[0]: cx23885 based dvb card
[   10.005877] DVB: registering new adapter (cx23885[0])
[   10.006591] cx23885_dev_checkrevision() Hardware revision = 0xb0
[   10.006606] cx23885[0]/0: found at 0000:02:00.0, rev: 2, irq: 16, latency: 0, mmio: 0xd0000000
[   10.006621] cx23885 0000:02:00.0: setting latency timer to 64

lspci:
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:00.0 Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 02)
0a:0b.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705_2 Gigabit Ethernet (rev 03)

---

### Post by bwooster0 on 2009-02-11
I am using Mythbuntu 8.10. I got the Dvico HDTV7 Dual Express card 3 days ago.

I got it work by doing the following.

1) Use the System update to get all current updates
2) Went to linuxtv.org and downloaded, compiled and install the latest V4L libraries / drivers
3) Downloaded the firmware for the device (used google to find it) and used "sudo sh extract.sh" in the terminal to get the firmware and then moved it into the /lib directory that the script suggested
4) restarted and went into the mythtv setup area to add in the new card - you can add it in twice to take advantage of the dual tuners

so far everything seems to be working

---

### Post by gavin0001 on 2009-02-18
Sorry for the delay with posting, other projects have got in the way :(. But anyway, thanks, I will rebuild and make sure i follow that. Will repost in a couple of days

---

### Post by Azzir on 2009-02-22
> **bwooster0 said:**
> I am using Mythbuntu 8.10. I got the Dvico HDTV7 Dual Express card 3 days ago.Just a quick caveat to anyone who happens to drop by here... the [DViCO HDTV7 Dual Express]("http://www.fusionhdtv.co.kr/ENG/products/HDTV7DualExpress.aspx") is NOT the same as the [DViCO HDTV Dual Express DVB-T]("http://www.fusionhdtv.co.kr/ENG/products/DVBTDualExpress.aspx").

I'm currently trying to set mine up on my Ubuntu 8.10 box and was a little bit confused for a while, so I hope this helps in some way :)

EDIT: Gavin0001: What guides have you been looking into? I'll be subscribing to this thread, so I'll keep you updated as I go if you'll do the same :)

---

### Post by bwooster0 on 2009-02-22
When I went to the "Capture cards" part of Mythtv set up I

1) added in my card as a "DVB DTV capture card(v3.x)" with device id 1
2) I then went to the "recording options" menu and set Max recordings to 1
3) I turned off the "active EIT scan" option (I have a schedules direct account)

Then I repeated the above steps adding in the same card with device id 2

---

### Post by gavin0001 on 2009-02-25
So I have rebuilt the Mythbuntu box, installed all of the current updates, and I have downloaded and installed mercurial and v4l. The card is now auto-detected at start up (The correct name appears in the dmesg log), and the MythTV system can see the tuners, however I still cannot tune. I believe (although I could quite possibly be wrong...) that it is a firmware issue related to the XCeive tuners. The card that I have has TWO XCeive 3028 Digital Tuners, and it has a Conexant cx23885 decoder chip. I have tried using the firmware from Chris Pascoe's site, however dmesg tells me that it thinks my card is a DViCO DualDig4/Nano2 (Australia). If I don't have anything in the firmware folder, dmesg entries say that 'xc3028-27.fw' cannot be found. Does anyone know where I might be able to obtain firmware for my card?? 

Please note that my card is a DViCO FusionHDTV Dual Express, NOT a DViCO FusionHDTV7.

@Azzir
The guide that I started following was [http://www.ethics-gradient.net/myth/mythdvb.html](http://www.ethics-gradient.net/myth/mythdvb.html) , however, it is not related exactly to the card (by 'not exactly' I mean not at all) but more a general overview on setting up Myth. From there I have just googled around to figure out bits and pieces along the way. I have some rough documentation of my process, so I can probably post that when I am finished. So there you have it, a long answer for a short question :p

---

### Post by xipmix on 2009-02-27
> **gavin0001 said:**
> ... I have tried using the firmware from Chris Pascoe's site, however dmesg tells me that it thinks my card is a DViCO DualDig4/Nano2 (Australia). If I don't have anything in the firmware folder, dmesg entries say that 'xc3028-27.fw' cannot be found. Does anyone know where I might be able to obtain firmware for my card?? 


Try Kemble Wagner's posts, start here: 
[http://ubuntuforums.org/showthread.php?t=616103](http://ubuntuforums.org/showthread.php?t=616103)
See also these threads on the linux-dvb list
[http://www.linuxtv.org/pipermail/linux-dvb/2008-August/027959.html](http://www.linuxtv.org/pipermail/linux-dvb/2008-August/027959.html)
and
[http://www.linuxtv.org/pipermail/linux-dvb/2008-August/028109.html](http://www.linuxtv.org/pipermail/linux-dvb/2008-August/028109.html)

> **gavin0001 said:**
> Please note that my card is a DViCO FusionHDTV Dual Express, NOT a DViCO FusionHDTV7.

can you show the PCI ID for the card - that will clarify things a lot for people reading this.
The command you need is "(lspci && lspci -n ) | sort". This will show the numeric PCI ID and the associated string, on successive lines.

If you have the card I think you do, you should see the PCI ID as "18ac:db78".
Support for this card went in to v4l about Aug 2008, see thread starting here
[http://www.linuxtv.org/pipermail/linux-dvb/2008-August/027523.html](http://www.linuxtv.org/pipermail/linux-dvb/2008-August/027523.html)

---

### Post by gavin0001 on 2009-03-01
"(lspci && lspci -n) | sort":
02:00.0 0400: 14f1:8852 (rev 02)
02:00.0 Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 02)

So at the moment, it would seem that I have a completely different card to what Kemble Wagner's posts are written for. I tested out the firmware that is included with Kemble Wagner's post, however when I attempt to tune, the dmesg log indicates that the firmware is corrupt. Does anyone know where else I might be able to obtain a copy of the required firmware?

I have also attached some segments of dmesg logs for those that are interested. There is one before I do system updates, one after, and one after I install v4l drivers. After I install the V4L drivers, the card is auto-detected with the correct product name. If I don't place any firmware in the /lib/firmware directory, dmesg will say that xc3028-v27.fw couldn't be found. "after_v4l&firmware.txt" contains the dmesg entries that indicate that the firmware is corrupt.

On an unrelated topic, when I update the linux headers, should I be removing the old ones??

---

### Post by enchesss on 2009-03-02
gavin

are you setting up the tuner properly by allocating a video source

just select no grabber in the vidoe source and name it

then go to the input connections and you should be bale to scan

see here:

[http://www.dvrplayground.com/article/13712/MythTV-Ubuntu-Installation-Guide/](http://www.dvrplayground.com/article/13712/MythTV-Ubuntu-Installation-Guide/)

---

### Post by gavin0001 on 2009-03-02
Yes I was doing that previously, however at the moment I am simply using dvb utils to attempt to create a channels.conf file, and I am still getting corrupted firmware messages in the dmesg log.

---

### Post by xipmix on 2009-03-04
Regarding firmware, this thread may help:
 [http://osdir.com/ml/linux-media/2009-01/msg00160.html](http://osdir.com/ml/linux-media/2009-01/msg00160.html)
in particular:
 [http://osdir.com/ml/linux-media/2009-01/msg00183.html](http://osdir.com/ml/linux-media/2009-01/msg00183.html)
and that lead to
 [http://www.linuxtv.org/wiki/index.php/Xceive_XC3028/XC2028#How_to_Obtain_the_Firmware](http://www.linuxtv.org/wiki/index.php/Xceive_XC3028/XC2028#How_to_Obtain_the_Firmware)

I found this via google:cx23885+firmware+v4l

Dropping the last search term turned up this:
  [http://bugs.gentoo.org/255421](http://bugs.gentoo.org/255421)
which points to pretty much the same place.

It seems worth trying to download the firmware from Steven Toth's site referenced in the links above. It may also be of use to post md5sums or sha1sums of the firmware files you have tried. "md5sum /lib/firmware/*" should do it.

Regarding headers - I think v4l will usually try to build against the kernel-headers for the currently running kernel, and installs modules into /lib/modules/`uname -r`. So as long as you have the kernel-headers-2.6.xx-* package installed where the 2.6.xx-* is the same version as the kernel you have booted, you should be ok. You shouldn't have to remove the old headers. ("uname -r" shows you the version number you are currently running.)

You may want to check there isn't generic symlink (/usr/src/linux, or /usr/src/linux-headers) pointing to some old version of the headers.

---

### Post by enchesss on 2009-03-04
gavin,

> however at the moment I am simply using dvb utils to attempt to create a channels.conf file

can you post the error from the utilities scan?

have you tried to open the channels config in vlc?

just go to quick open file and choose the channels.conf file


you need to stop the mythtv backend server first or it will give errors - (a highly frusturating experience)

just type /etc/init.d/mthytv-backend - stop


post the results. In vlc you should be able to change channels by opening the playlist.

if this is successful then exit vlc and restart myth
let us know

---

### Post by brucesky on 2009-03-11
Hi there Gavin et al...

I happen to be in a similar situation with you. I am using exactly the same card (DViCO FusionHDTV Dial Express) and I am located in Melbourne, Australia. I am trying to convert my existing PC into a PVR, so it can be "put out to pasture" next to my TV, when I buy a swanky new piece of kit.

However, I am experiencing frustrations with the tuning as well. I first tried Mythbuntu (Intrepid 8.10), but because I am a N00B (i.e. Being an IT professional I think I know what I am doing, but I need a tap on the shoulder) I tied myself in knots and had to re-install Kubuntu (8.10 AMD64 desktop) instead. Nearly lost Windows Vista by screwing with the partitions :oops: but "just" saved myself from complete misery. I then picked myself up and got Kubuntu installed. Everything worked, I even got Skype (including my webcam) working so I was feeling confident. Always a dangerous emotion at 11:30pm when I have to work the next day.

So I went to the linuxtv.org website and downloaded the V4L-DVB drivers. I did the make and make install steps. I also found the latest version of the firmware and placed it in the firmware directory. Ok, reboot [-o<

Then, Kubuntu crashed on startup! #-o
I must have done something wrong, and I hope that I don't have to re-install again. I will attempt to back out the firmware change (maybe it's corrupted). I'm not sure what is wrong, because in my first Mythbuntu attempt I managed to get the card recognised. However, I didn't realise that you could test the card with other software. Silly me...

Hopefully one of us will crack through this problem soon.

Sorry for the wordy response, but I am at work (clearly distracted)...

Cheers,
Bruce

---

### Post by gavin0001 on 2009-03-16
Good News Everyone!
 
Got it working, so I thought I'd post back here so that other people can benefit. First of all, I just want to let anyone who is reading this know that the following information is for anyone with the card id 14f1:8852 (rev 02). This can be found by using "(lspci && lspci -n) | sort" (without the quote marks). A Sample output of this command would look something like this:
*<cut>*
```
02:00.0 0400: 14f1:8852 (rev 02)
02:00.0 Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 02)
```
*<cut>*
 
So anyway, back to the story... Spent another couple of hour's googling and stumbled across this link: [http://www.linuxtv.org/wiki/index.php/DViCO_FusionHDTV_DVB-T_Dual_Express](http://www.linuxtv.org/wiki/index.php/DViCO_FusionHDTV_DVB-T_Dual_Express). This page states that while card is not officially supported, it has *experimental* support. I have discovered that while the main v4l drivers detect the card, for some reason it doesn't work. However, using Steven Toth's drivers, and the xc3028-v27.fw file, it seems to work fine. I have included a command list to install this card below(I used CODE tags, as that seemed to be the best way to represent the list):
***Make sure that mythbuntu has all of the current updates, including the latest headers.***
```
apt-get install mercurial build-essential linux-headers-`uname -r`
sudo apt-get install unzip
sudo apt-get install dvb-utils
mkdir firmware
cd firmware/
wget http://www.steventoth.net/linux/xc5000/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip
unzip -j HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip Driver85/hcw85bda.sys
cp /usr/src/linux/Documentation/video4linux/extract_xc3028.pl .
./extract_xc3028.pl
/* Don't copy the firmware just yet.... */
cd ..
hg clone http://linuxtv.org/hg/~stoth/v4l-dvb/
cd v4l-dvb
sudo make && make install
sudo cp firmware/xc3028-v27.fw /lib/firmware
sudo reboot
...
dmesg | grep cx23885
ls /dev/dvb
```
Basically all that needs to be checked here is that the dvb folder is populated with adapter0 and adapter1 folders. If that checks out OK, proceed on. You will need to substitute your place of residence in the scan command if you're not in Brisbane.
If you've configured mythtv to use the TV adapters already, you will need to stop the backend, which can be done using "sudo /etc/init.d/mythtv-backend stop"
```
scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/au-Brisbane > channels.conf
cat channels.conf
```
Check that the channels.conf file is populated. I didn't use this file to put channels into mythtv, but I think it's possible to do so. I simply used this to check that tuning completed correctly. At this stage, I was not able to tune Channel 10 in Brisbane, but I suspect that is due to the location of the antenna I'm using, so I will have to manually enter that.
After this, launch the MythTV Backend Setup, and proceed with configuration/tuning/etc.... Please don't forget to run mythfill-database, you will be prompted at the completion of the backend setup process.
 
I think I have included everything, however, if I've forgotten anything, please let me know so that I can update this post. Also, I am hoping that the above order is OK, as this wasn't quite how I did it (My way involved a lot more testing, rebooting, downloading, and the occasional bit of swearing :D), so if you find that this doesn't work, please let me know and I will make the necessary changes. In any case, will most likely rebuild the machine to make sure it is fresh.
I haven't yet managed to get the remote working, but this is on my to-do list, will update when I have it working.
 
References:
-[http://linuxtv.org/wiki/index.php/How_to_Obtain%2C_Build_and_Install_V4L-DVB_Device_Drivers]("http://linuxtv.org/wiki/index.php/How_to_Obtain%2C_Build_and_Install_V4L-DVB_Device_Drivers")
-[http://linuxtv.org/wiki/index.php/Xceive_XC3028/XC2028]("http://linuxtv.org/wiki/index.php/Xceive_XC3028/XC2028")
-[http://www.linuxtv.org/wiki/index.php/DViCO_FusionHDTV_DVB-T_Dual_Express]("http://www.linuxtv.org/wiki/index.php/DViCO_FusionHDTV_DVB-T_Dual_Express")
-[http://www.linuxtv.org/wiki/index.php/Scan]("http://www.linuxtv.org/wiki/index.php/Scan")-[http://www.linuxtv.org/wiki/index.php/Testing_your_DVB_device]("http://www.linuxtv.org/wiki/index.php/Testing_your_DVB_device")

---

### Post by xipmix on 2009-03-22
> **gavin0001 said:**
> Good News Everyone!
 
"(lspci && lspci -n) | sort" (without the quote marks). A Sample output of this command would look something like this:
*<cut>*
```
02:00.0 0400: 14f1:8852 (rev 02)
02:00.0 Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 02)
```

Nice work.

It's worth pointing out that the kernel sees the DViCO bits as a subsystem on this card, with a different PCI ID:
```

# dmesg|grep -i dvico
 CORE cx23885[0]: subsystem: 18ac:db78, board: DViCO FusionHDTV DVB-T Dual Express [card=11,autodetected]
# lspci -vmm -s 04:00
Slot:   04:00.0
Class:  Multimedia video controller
Vendor: Conexant Systems, Inc.
Device: CX23885 PCI Video and Audio Decoder
SVendor:        DViCO Corporation
SDevice:        Unknown device db78
Rev:    02

# lspci -vmmn -s 04:00
Slot:   04:00.0
Class:  0400
Vendor: 14f1
Device: 8852
SVendor:        18ac
SDevice:        db78
Rev:    02

```
This might be where the confusion about Kemble Wagner's posts came from?

The subsystem arrangement seems somewhat backwards to me, ie since the board is manufactured/branded by DViCO I would have expected to see the Conexant chips as a subsystem, e.g.

```

Slot:   04:00.0
Class:  0400
Vendor: 18ac
Device: db78
Rev:    02
SVendor:        14f1
SDevice:        8852

```
or something. But I digress.

The kernel on the other hand knows about the device (see [http://linuxtv.org/hg/~stoth/v4l-dvb/rev/d61c3d922e98](http://linuxtv.org/hg/~stoth/v4l-dvb/rev/d61c3d922e98))
```
[   48.940731] cx23885 driver version 0.0.1 loaded
[   48.940787] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 19 (level,low)-> IRQ 19
[   48.940800] CORE cx23885[0]: subsystem: 18ac:db78, board: DViCO FusionHDTV DVB-T Dual Express [card=11,autodetected]

and, a bit later...
[   49.082921] DVB: registering new adapter (DViCO FusionHDTV DVB-T Dual Digital 4)
[   49.144201] input: i2c IR (FusionHDTV) as /devices/virtual/input/input6
[   49.158982] ir-kbd-i2c: i2c IR (FusionHDTV) detected at i2c-1/1-006b/ir0 [cx23885[0]]
[   49.159771] cx23885_dvb_register() allocating 1 frontend(s)
[   49.159774] cx23885[0]: cx23885 based dvb card
[   49.188272] xc2028 1-0061: creating new instance
[   49.188275] xc2028 1-0061: type set to XCeive xc2028/xc3028 tuner
[   49.188278] DVB: registering new adapter (cx23885[0])
[   49.188281] DVB: registering adapter 1 frontend 0 (Zarlink ZL10353 DVB-T)...
[   49.188453] cx23885_dvb_register() allocating 1 frontend(s)
[   49.188455] cx23885[0]: cx23885 based dvb card
[   49.188993] xc2028 2-0061: creating new instance
[   49.188995] xc2028 2-0061: type set to XCeive xc2028/xc3028 tuner
[   49.188998] DVB: registering new adapter (cx23885[0])
[   49.189000] DVB: registering adapter 2 frontend 0 (Zarlink ZL10353 DVB-T)...
[   49.189161] cx23885_dev_checkrevision() Hardware revision = 0xb0
[   49.189167] cx23885[0]/0: found at 0000:04:00.0, rev: 2, irq: 19, latency: 0, mmio: 0x90000000
[   49.189173] PCI: Setting latency timer of device 0000:04:00.0 to 64


```
I don't know if the hardware revision (0xb0) matters.

I've sent a patch for the "unknown" device to pciids.sf.net.

---

### Post by infirmus on 2009-04-29
Arghh, its hell trying to get this card working. I am using a custom compiled 2.6.29.2 kernel which has built in v4l-dvb modules but i have tried compiling the modules from Steven Toths repository as well but I get the same result. I have also tried going back to the Jaunty default generic kernel to no avail.

Keeps saying "Incorrect readback of firmware version" when I try to tune.

I wonder if the "Hardware revision unknown 0x0" message has something to do with it. The dmesg outputs from everyone else seems to indicate that they have hardware revision "0xb0".

Relevant dmesg output:
```
[   11.918610] cx23885 driver version 0.0.1 loaded
[   11.918658] cx23885 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   11.918831] CORE cx23885[0]: subsystem: 0000:0000, board: DViCO FusionHDTV DVB-T Dual Express [card=11,insmod option]
[   12.097153] input: i2c IR (FusionHDTV) as /devices/virtual/input/input6
[   12.132588] ir-kbd-i2c: i2c IR (FusionHDTV) detected at i2c-0/0-006b/ir0 [cx23885[0]]
[   12.141819] cx23885_dvb_register() allocating 1 frontend(s)
[   12.141823] cx23885[0]: cx23885 based dvb card
[   12.215040] xc2028 0-0061: creating new instance
[   12.215042] xc2028 0-0061: type set to XCeive xc2028/xc3028 tuner
[   12.215047] DVB: registering new adapter (cx23885[0])
[   12.215050] DVB: registering adapter 0 frontend 0 (Zarlink ZL10353 DVB-T)...
[   12.215302] cx23885_dvb_register() allocating 1 frontend(s)
[   12.215304] cx23885[0]: cx23885 based dvb card
[   12.215899] xc2028 1-0061: creating new instance
[   12.215900] xc2028 1-0061: type set to XCeive xc2028/xc3028 tuner
[   12.215903] DVB: registering new adapter (cx23885[0])
[   12.215904] DVB: registering adapter 1 frontend 0 (Zarlink ZL10353 DVB-T)...
[   12.216092] cx23885_dev_checkrevision() New hardware revision found 0x0
[   12.216094] cx23885_dev_checkrevision() Hardware revision unknown 0x0
[   12.216100] cx23885[0]/0: found at 0000:03:00.0, rev: 4, irq: 19, latency: 0, mmio: 0xfa000000
[   12.216107] cx23885 0000:03:00.0: setting latency timer to 64
[   92.688454] i2c-adapter i2c-0: firmware: requesting xc3028-v27.fw
[   92.726959] xc2028 0-0061: Loading 80 firmware images from xc3028-v27.fw, type: xc2028 firmware, ver 2.7
[   92.925583] xc2028 0-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[   94.073958] xc2028 0-0061: Loading firmware for type=D2633 DTV7 (90), id 0000000000000000.
[   94.087744] xc2028 0-0061: Loading SCODE for type=DTV6 QAM DTV7 DTV78 DTV8 ZARLINK456 SCODE HAS_IF_4760 (620003e0), id 0000000000000000.
[   94.121376] xc2028 0-0061: Incorrect readback of firmware version.
[   94.375433] xc2028 0-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[   95.525964] xc2028 0-0061: Loading firmware for type=D2633 DTV7 (90), id 0000000000000000.
[   95.539937] xc2028 0-0061: Loading SCODE for type=DTV6 QAM DTV7 DTV78 DTV8 ZARLINK456 SCODE HAS_IF_4760 (620003e0), id 0000000000000000.
[   95.569386] xc2028 0-0061: Incorrect readback of firmware version.
[   96.011128] xc2028 0-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[   97.157933] xc2028 0-0061: Loading firmware for type=D2633 DTV7 (90), id 0000000000000000.
[   97.171933] xc2028 0-0061: Loading SCODE for type=DTV6 QAM DTV7 DTV78 DTV8 ZARLINK456 SCODE HAS_IF_4760 (620003e0), id 0000000000000000.
[   97.205376] xc2028 0-0061: Incorrect readback of firmware version.
```
lspci:
```
03:00.0 0400: 14f1:8852 (rev 04)
03:00.0 Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 04)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 19
	Region 0: Memory at fa000000 (64-bit, non-prefetchable) [size=2M]
	Capabilities: [40] Express (v1) Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
			ExtTag- AttnBtn- AttnInd- PwrInd- RBE- FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <2us, L1 <4us
			ClockPM- Suprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk-
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
	Capabilities: [80] Power Management version 2
		Flags: PMEClk- DSI+ D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [90] Vital Product Data <?>
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [200] Virtual Channel <?>
	Kernel driver in use: cx23885
	Kernel modules: cx23885


```

---

### Post by infirmus on 2009-04-29
Hmm. OK Just got it working.. Guess how, by compiling the latest hg version of v4l-dvb. Funny that ;)

Just to re-iterate, the Steven Toth drivers from [http://linuxtv.org/hg/~stoth/v4l-dvb/](http://linuxtv.org/hg/~stoth/v4l-dvb/) did not work for me only the drivers from the main repository at [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)

---

### Post by gidsmyth on 2009-08-15
G'day all
 
I have been having similar problems in that I cannot get mythtv (or other scan programs) to detect any channels with this card. I have tried to use both stoth and linux tv sources to no avail. Being a linux noob I'm happy to accept I have done it wrong and start over if someone can take a look and see if the below output flags any problems. A previous post on here from me lead some one to think that the cx88 module was not loading correctly?
 
When I follow the procedures outline in this tread I basically start running into problems with the line:
sudo cp firmware/xc3028-v27.fw /lib/firmware
 
I get a 'file not found error' which makes me think that 
perl ./extract_xc3028.pl 
is not working. Especially when I do a file search for 'xc3028-v27.fw' , its nowhere on the machine.
 
Anyway the output is below so please take a look
 
Thank you
 
output:
 
sudo lspci -v
 
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
Subsystem: ASUSTeK Computer Inc. Device 826d
Flags: bus master, 66MHz, medium devsel, latency 64
 
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
Flags: bus master, 66MHz, medium devsel, latency 99
Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
I/O behind bridge: 0000c000-0000cfff
Memory behind bridge: fdd00000-fdefffff
Prefetchable memory behind bridge: 00000000f0000000-00000000f7ffffff
Capabilities: [44] HyperTransport: MSI Mapping Enable+ Fixed+
Capabilities: [b0] Subsystem: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
Kernel modules: shpchp
 
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
I/O behind bridge: 0000e000-0000efff
Memory behind bridge: fd600000-fd7fffff
Prefetchable memory behind bridge: 00000000fda00000-00000000fdafffff
Capabilities: [50] Power Management version 3
Capabilities: [58] Express Root Port (Slot-), MSI 00
Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
Capabilities: [b0] Subsystem: ASUSTeK Computer Inc. Device 826d
Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
Capabilities: [100] Virtual Channel <?>
Kernel driver in use: pcieport-driver
Kernel modules: shpchp
 
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
I/O behind bridge: 0000d000-0000dfff
Memory behind bridge: fd900000-fd9fffff
Prefetchable memory behind bridge: 00000000fdf00000-00000000fdffffff
Capabilities: [50] Power Management version 3
Capabilities: [58] Express Root Port (Slot-), MSI 00
Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
Capabilities: [b0] Subsystem: ASUSTeK Computer Inc. Device 826d
Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
Capabilities: [100] Virtual Channel <?>
Kernel driver in use: pcieport-driver
Kernel modules: shpchp
 
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA (prog-if 01)
Subsystem: ASUSTeK Computer Inc. Device 81ef
Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
I/O ports at ff00 [size=8]
I/O ports at fe00 [size=4]
I/O ports at fd00 [size=8]
I/O ports at fc00 [size=4]
I/O ports at fb00 [size=16]
Memory at fe02f000 (32-bit, non-prefetchable) [size=1K]
Capabilities: [60] Power Management version 2
Kernel driver in use: ahci
 
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) (prog-if 10)
Subsystem: ASUSTeK Computer Inc. Device 81ef
Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
Memory at fe02e000 (32-bit, non-prefetchable) [size=4K]
Kernel driver in use: ohci_hcd
 
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) (prog-if 10)
Subsystem: ASUSTeK Computer Inc. Device 81ef
Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
Kernel driver in use: ohci_hcd
 
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2) (prog-if 10)
Subsystem: ASUSTeK Computer Inc. Device 81ef
Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
Kernel driver in use: ohci_hcd
 
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) (prog-if 10)
Subsystem: ASUSTeK Computer Inc. Device 81ef
Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
Kernel driver in use: ohci_hcd
 
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) (prog-if 10)
Subsystem: ASUSTeK Computer Inc. Device 81ef
Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
Memory at fe02a000 (32-bit, non-prefetchable) [size=4K]
Kernel driver in use: ohci_hcd
 
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) (prog-if 20)
Subsystem: ASUSTeK Computer Inc. Device 81ef
Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
Memory at fe029000 (32-bit, non-prefetchable) [size=256]
Capabilities: [c0] Power Management version 2
Capabilities: [e4] Debug port: BAR=1 offset=00e0
Kernel driver in use: ehci_hcd
 
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
Subsystem: ASUSTeK Computer Inc. Device 81ef
Flags: 66MHz, medium devsel
I/O ports at 0b00 [size=16]
Capabilities: [b0] HyperTransport: MSI Mapping Enable- Fixed+
Kernel driver in use: piix4_smbus
Kernel modules: i2c-piix4
 
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE (prog-if 8a [Master SecP PriP])
Subsystem: ASUSTeK Computer Inc. Device 81ef
Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
I/O ports at 01f0 [size=8]
I/O ports at 03f4 [size=1]
I/O ports at 0170 [size=8]
I/O ports at 0374 [size=1]
I/O ports at f900 [size=16]
Kernel driver in use: pata_atiixp
 
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
Subsystem: ASUSTeK Computer Inc. Device 8249
Flags: bus master, slow devsel, latency 64, IRQ 16
Memory at fe020000 (64-bit, non-prefetchable) [size=16K]
Capabilities: [50] Power Management version 2
Kernel driver in use: HDA Intel
Kernel modules: snd-hda-intel
 
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
Subsystem: ASUSTeK Computer Inc. Device 81ef
Flags: bus master, 66MHz, medium devsel, latency 0
 
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
Bus: primary=00, secondary=04, subordinate=04, sec-latency=64
I/O behind bridge: 0000b000-0000bfff
Memory behind bridge: fdc00000-fdcfffff
Prefetchable memory behind bridge: fdb00000-fdbfffff
 
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
Flags: fast devsel
Capabilities: [80] HyperTransport: Host or Secondary Interface
 
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
Flags: fast devsel
 
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
Flags: fast devsel
 
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
Flags: fast devsel
Capabilities: [f0] Secure device <?>
Kernel driver in use: k8temp
Kernel modules: k8temp
 
01:05.0 VGA compatible controller: ATI Technologies Inc RS690 [Radeon X1200 Series]
Subsystem: ASUSTeK Computer Inc. Device 826d
Flags: bus master, fast devsel, latency 64, IRQ 18
Memory at f0000000 (64-bit, prefetchable) [size=128M]
Memory at fdef0000 (64-bit, non-prefetchable) [size=64K]
I/O ports at ce00 [size=256]
Memory at fdd00000 (32-bit, non-prefetchable) [size=1M]
Capabilities: [50] Power Management version 2
Capabilities: [80] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
:confused::confused:
02:00.0 Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 02)
Subsystem: DViCO Corporation Device db78
Flags: bus master, fast devsel, latency 0, IRQ 18
Memory at fd600000 (64-bit, non-prefetchable) [size=2M]
Capabilities: [40] Express Endpoint, MSI 00
Capabilities: [80] Power Management version 2
Capabilities: [90] Vital Product Data <?>
Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
Capabilities: [100] Advanced Error Reporting <?>
Capabilities: [200] Virtual Channel <?>
Kernel driver in use: cx23885
Kernel modules: cx23885
 
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
Subsystem: ASUSTeK Computer Inc. Device 81aa
Flags: bus master, fast devsel, latency 0, IRQ 2301
I/O ports at de00 [size=256]
Memory at fd9ff000 (64-bit, non-prefetchable) [size=4K]
[virtual] Expansion ROM at fdf00000 [disabled] [size=128K]
Capabilities: [40] Power Management version 2
Capabilities: [48] Vital Product Data <?>
Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
Capabilities: [60] Express Endpoint, MSI 00
Capabilities: [84] Vendor Specific Information <?>
Capabilities: [100] Advanced Error Reporting <?>
Capabilities: [12c] Virtual Channel <?>
Capabilities: [148] Device Serial Number 68-81-ec-10-00-00-00-1a
Capabilities: [154] Power Budgeting <?>
Kernel driver in use: r8169
Kernel modules: r8169
---------------------------
(before i messed about following this thread)
dmesg | grep xc 
[ 0.404105] pci 0000:01:05.0: reg 20 io port: [0xce00-0xceff]
[ 0.404125] pci 0000:00:01.0: bridge io port: [0xc000-0xcfff]
[ 0.458734] system 00:01: ioport range 0xc00-0xc01 has been reserved
[ 0.458736] system 00:01: ioport range 0xc14-0xc14 has been reserved
[ 0.458738] system 00:01: ioport range 0xc50-0xc52 has been reserved
[ 0.458740] system 00:01: ioport range 0xc6c-0xc6d has been reserved
[ 0.458742] system 00:01: ioport range 0xc6f-0xc6f has been reserved
[ 0.458744] system 00:01: ioport range 0xcd0-0xcd1 has been reserved
[ 0.458746] system 00:01: ioport range 0xcd2-0xcd3 has been reserved
[ 0.458748] system 00:01: ioport range 0xcd4-0xcdf has been reserved
[ 0.458769] system 00:0d: iomem range 0xcd600-0xcffff has been reserved
[ 0.463443] pci 0000:00:01.0: IO window: 0xc000-0xcfff
[ 0.463509] bus: 01 index 0 io port: [0xc000-0xcfff]
[ 4.138221] powernow-k8: 2 : fid 0xe (2200 MHz), vid 0xc
[ 4.138223] powernow-k8: 3 : fid 0xc (2000 MHz), vid 0xe
[ 10.341777] xc2028 1-0061: creating new instance
[ 10.341780] xc2028 1-0061: type set to XCeive xc2028/xc3028 tuner
[ 10.342705] xc2028 2-0061: creating new instance
[ 10.342706] xc2028 2-0061: type set to XCeive xc2028/xc3028 tuner
 
(after messing about as above plus numerous versions of the following pairs)
[ 1199.206971] i2c-adapter i2c-1: firmware: requesting xc3028-v27.fw
[ 1199.215194] xc2028 1-0061: Error: firmware xc3028-v27.fw not found.
 
------------------------------
dmesg|grep -i dvico
[ 7.433147] CORE cx23885[0]: subsystem: 18ac:db78, board: DViCO FusionHDTV DVB-T Dual Express [card=11,autodetected]
---------------------------------
 
lspci -vmm -s 02:00
Slot: 02:00.0
Class: Multimedia video controller
Vendor: Conexant Systems, Inc.
Device: CX23885 PCI Video and Audio Decoder
SVendor: DViCO Corporation
SDevice: Device db78
Rev: 02
---------------------------------
lspci -vmmn -s 02:00
Slot: 02:00.0
Class: 0400
Vendor: 14f1
Device: 8852
SVendor: 18ac
SDevice: db78
Rev: 02

---

### Post by gavin0001 on 2009-08-15
Hi gidsmyth,

I rebuilt the mythtv box I was working on a couple of months ago, which I was always planning to do before I put it into use, but the project stopped for quite some time. When I was rebuilding it, I made a mistake and downloaded the linux tv source instead, and it now seems to work. But anyway, small sidenote.

I do remember having your exact same problem, but I can't remember what I did to solve it. If the extract script is not working (which as you correctly pointed out, it probably isn't seeing as there is no xc3028-v27.fw file), my only guess would be that the zip file is not there/not extracted. Did you have any issues getting the zip file or unzipping (it's a few lines back from where you're having an error). Inside the fimware directory before you run the extract script, there should be the extract script, and hcw85bda.sys and the downloaded zip archive. Is that what you have, or did you extract the whole archive? After you run the script, check what is in the directory and make sure it actually created the firmware file.

Have fun. Let us know how it goes:popcorn:

---

### Post by gidsmyth on 2009-08-15
Good morning!
 
This is where it does get interesting I guess. The .zip definately downloaded. The unzip didn't record any errors (that I recall) but the only file that appeared into the directory was hcw85bda.sys (which is correct as I understand the commands used)
I then went hunting for the extract file which was not under the file path you suggested, but I found one under 
/usr/src/linuxheaders-2.6.28-14/Documentation/video4linux/extract_xc3028.pl
I then manually copied this to the newly created firmware directory
btw I had at least two linuxheaders directories, and this appeared to be the most recent, but again I could have been wrong here.
 
I admit I perhaps didn't fully understand the suggested commands as 'cp /usr/src/linux/Documentation/video4linux/extract_xc3028.pl'
gave me an error asking for a destination (so I assumed it should be the firmware directory) and 
'./extract_xc3028.pl'
didn't run so I had to dig around before I realised it is a perl script and would run if I used
'perl ./extract_xc3028.pl'
 
To set the context more clearly I am running a Mythbuntu 9.04 which I fully updated before trying what you suggested. I hadn't killed the backend before doing it all but would that have made a difference at this point? I have also had to modify how mythtv loads due to an ATI graphics chipset, but I can't see how that would have affected what I 'm doing to the firmware.
 
Thanks!

---

### Post by gavin0001 on 2009-08-16
Hi gidsmyth,

Where are you making the firmware directory?? I just made it inside the home directory, it shouldn't be the /lib/firmware directory. I then cd'ed into it and then copied the perl script. The copy statement should have had a . on the end, to signify copy into the current directory. The script should execute without needing to call the perl executable, as the path to the executable is specified in the first line of any script. You might just need to change the permissions on it, which can be done which chmod +x extract_xc3028.pl Extract (or move) the hcw85bda.sys and try running the script again. As for the location of the script, that is probably right, I was using 8.10 when I worked that out, so it may have changed.

Just to check also, you're on a 32 bit machine right??

Let me know how you go.

---

### Post by gidsmyth on 2009-08-16
Firmware is off the home dir.
The machine is 64bit....is that going to make much difference?
I'll try again with chmod cmd now
 
Thanks
 
EDIT
Changing the permissions didn't seem to make much difference. It again ran the 'extract_xc3028.pl' and gave the message 'Firmwares generated' but no additional files were added to the directory. (*thinking out loud try the other 'extract_xc3028.pl' files perhaps*)

---

### Post by gidsmyth on 2009-08-16
Ok progress perhaps?
Following my last post I re-downloaded the v4l-dvb stuff from the linux-tv link mentioned in this thread. I then found:

/home/myth-server/v4l-dvb/v4l2-apps/util
contains a directory 
'xc3028 firmware'
this contains:

extract_head.h
firmware-tool.c
Makefile
Readme                                                         ..............................which I read but don't understand
standards.c
standards.h

First question: Is this useful?
2nd: If so....how do I use it!?!

The read me says:
Firmware dumps must be in ASCII format and each line corresponds to an I2C instruction sent to the chip. Each line must either be a special instruction like RESET_CLK, RESET_TUNER (see standards.c) or be a sequence of bytes represented in hexadecimal format xx separated by a space character ' '.

:confused:
Thanks

---

### Post by gavin0001 on 2009-08-16
Hi gidsmyth,

Am not sure how the f/w will go on the 64 bit system, but I suspect it might be the cause of your issues. It might be worth having a poke around the downloaded zip file and work out where the 64 bit stuff is (am fairly sure it is under drivers/64bit or something silly like that) and extract the 64bit hcw85bda.sys then try running the script again. (For kicks if nothing else :)). Am not sure how the util stuff is useful, but I will have a good look tomorrow or tuesday if I get some spare time.

Let me know how you go.

---

### Post by windoze killa on 2009-08-16
Hi all,
        I think I am about to embark on a severe hair removal process. Not only am I going to try and set up one of these cards I also have a Fusion Dual Digital 4 (Rev 2 :() that is installed. I have had no end of trouble trying to get these working in Vista 32 so thought I would try something stable. BUT going by the above I may just buy a STB. 

I will let you know how I get on.

PS. Linux will be great once all this sort of stuff happens automagically.

---

### Post by gidsmyth on 2009-08-17
Hello again

fully inflating the zip file does not obviously reveal any 64 bit directories but the files marked  :confused: might be them? Do I need to rename something and rerun the extract perhaps? Messing around at this level is beyond me even in windows :(

Otherwise has anyone found another zip file somewhere that might hold the 64bit stuff?

If worse comes to worse I'll rebuild with 32 bit but i'd rather work it a bit longer...
--------------------------------------

Archive:  HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip
replace hcw85bda.sys? [y]es, [n]o, [A]ll, [N]one, [r]ename: A
  inflating: hcw85bda.sys            
  inflating: hcw85enc.ax             
  inflating: hcw85prop.ax            
  inflating: hcwCP.ax                
  inflating: hcwECPPP.ax             
  inflating: hcw85bda.sys            
  inflating: hcw85enc.ax             
  inflating: hcw85enc.rom            
  inflating: hcw85mlC.rom            
  inflating: hcw85prop.ax            
  inflating: hcwCP.ax                
  inflating: hcwECPPP.ax             
  inflating: hcwxds.dll              
  :confused:inflating: hcw85b64.cat            
 :confused: inflating: hcw85b64.inf            
  inflating: hcw85bda.cat            
  inflating: hcw85bda.inf            
  inflating: hcwclear.exe            
  inflating: HcwDriverInstall.exe

---

### Post by gavin0001 on 2009-08-17
Hi gidsmyth,

Delete all of the extracted files and try this:

unzip -j HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip Driver85/64bit/hcw85bda.sys

I had a look at the archive (the one i downloaded at least) and there is a 64 bit directory, it would seems yours has to, as there seems to be 2 hcw85bda.sys files in your output. Not sure if it'll work, but worth a shot I guess.

Keep me posted :popcorn:

PS. windoze killa, if you're running a 32bit platform, you should have no problems, just follow the instructions (if they apply to your card) earlier in the thread). The issue at the moment is the 64 bit platform.

---

### Post by gidsmyth on 2009-08-17
:( all I got was the error message:

Hash of extracted file does not match (found 38e209de62964fdfbd3665c89cc4f2ba, expected 0e44dbf63bb0169d57446aec21881ff2!

So I downloaded the zip again just to make sure and tried it all again. Same error message. I notice that the zip was updated in May. When did you download it? I presume before that since you fixed your problem in March.

---

### Post by windoze killa on 2009-08-17
Ok guys, I hope it is as easy as you say. I will have a big go on the weekend. First problem I have found is when I run lspci it doesn't show any dvico devices. I ran lsusb and it says there are 2 instances of a dvico db98 there which I believe to be the Dual Digital 4. Any ideas why I can't see the Dual express?

---

### Post by gavin0001 on 2009-08-17
Hi gidsmyth,

what happens if you use the downloaded xc3028-v27.fw file from [http://ubuntuforums.org/showthread.php?t=616103](http://ubuntuforums.org/showthread.php?t=616103) ?? If you extract that and put it in /lib/firmware that should at least fix your not found error. I only just thought it :-k

---

### Post by gidsmyth on 2009-08-18
Gavin = genius
:guitar:
 
Look to be honest I had searched for xc3028-v27.fw and varients thereof, but I don't know why I couldn't find it. Probably had other terms like DVICO etc in there as well. I also think that I was getting errors using the command lines but the error messages were either false or misleading as when I went to copy the file downloaded last night to \lib\firmware i was getting errors using the terminal, but using a GUI found a copy already there that had the same date stamps as the new copy. Didn't take risks though so overwrote with the new and rebooted.
 
I would not be surprised if the 64bit issue was the reason that the unzip and extract was not playing nice, but for the moment I am happy as. 
 
**For other 64 bit users with this card on Mythbuntu 9.04 I recommend just downloading the xc3028-v27.fw directly rather than trying to extract it.**
 
Issues remaining for me:
1. Scheduler - about to set up shepherd so that shouldn't be 'too' hard
2. jerky picture - crap graphics card is my guess, but this is mostly to run as a backend 
3. finding another project to flail about in futility over! - hmm wonder what will happen if I.......](*,)
 
Thanks for all the cheese!
:popcorn:

---

### Post by gavin0001 on 2009-08-18
w00t.

Glad it's working now :)
If you can, either try the antenna in another location or put a signal amplifier in, as the jerky picture might be a signal quality/strength thing.

Have fun :)

---

### Post by gidsmyth on 2009-08-20
Hi Gavin,

To save myself some effort and useless hours of searching, did you configure the remote fully? If so which guide did you follow as I note there are many but all I have found are for earlier versions.

Cheers

---

### Post by gavin0001 on 2009-09-09
Hi gidsmyth,

Sorry for the slow reply, have been busy with other projects the last couple of weeks. Short answer is no, I never really put much effort into getting the remote control working, however, this link [http://ubuntuforums.org/showthread.php?t=616103](http://ubuntuforums.org/showthread.php?t=616103) might be a good starting point.

---

### Post by rommel74 on 2009-12-18
Hi all,

I'm happy to report that this card now works (almost) out of the box with Karmic Koala (and most likely other distros with the latest kernel).
All that is required is to copy the extracted firmware (found at the beginning of this thread) to /lib/firmware.

Yep, no more compiling drivers after every kernel update.

Tested on x64 Karmic Koala and MythTV

---

### Post by neilevan814 on 2009-12-23
You are referring still to the [DViCO FusionHDTV7 Dual Express? ]("http://www.mythtv.org/wiki/DViCO_FusionHDTV7_Dual_Express")
The mythtv.org site had reported they could not get the drivers for ntsc(analog) working only the digital signals.  Is this still the case or has the latest kernel and firmware resolved this issue?

---

### Post by gidsmyth on 2010-02-20
Neileven,
We are discussing a different DVICO card, NOT the HDTV7 version. I'm not sure if **DViCO FusionHDTV Dual Express** was ever sold in the US.
 
 
rommel 74,
Thanks for the heads up. I just did a clean install of 9.10 and it was like magic compared to last time! (ok so i kinda know what i'm doing, but hey).
I do have to rework the remote still, but i'm thinking that instead of adding another remote to my coffee table i might make my coffee table INTO the remote.....
[http://www.maximumpc.com/article/features/maximum_pc_builds_a_multitouch_surface_computer?page=0%2C0]("http://www.maximumpc.com/article/features/maximum_pc_builds_a_multitouch_surface_computer?page=0%2C0")
and make the unit into a front end with the TV as a second monitor!
 
Wish me luck!

---

### Post by Canarygsr on 2011-03-21
i get the following error when running make...

/home/nicholas/v4l-dvb/v4l/config-compat.h:4: fatal error: linux/autoconf.h: No such file or directory

---

