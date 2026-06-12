---
title: "how to get Dvico Fusionhdtv to work"
date: 2008-07-29
forum: Multimedia Software
---

### Post by Stolea on 2008-07-29
Silly question for day:
I have a Dvico FusionHDTV DVB-T Hybrid (Australian release of the DVBT-Plus card) card that I would like to be able to use in Ubuntu. I have tried to make sense of the available information and am now less enlightened than before I started on what steps I have to take.
Do I have to install Mythbuntu or can I run it from Ubuntu and what application will run it?
I use Ubuntu 8.04 with the current patches and a check tells me that the card is there and recognized.

---

### Post by Stolea on 2008-07-30
Anyone with any suggestions??

---

### Post by qhaz on 2008-07-30
. . . I share your pain.

Firstly you DON'T need Mythbuntu.  Simply install me-tv

[sudo] apt-get install me-tv

Apart from having to make your own channels.conf this program works just great.

To setup my DVICO stuff.
I can get it to work on my laptop using Hardy and kernel 2.6.24-19-generic by the following.

[sudo] apt-get install mercurial linux-headers-$(uname -r) build-essential 

hg clone [http://linuxtv.org/hg/~pascoe/xc-test/](http://linuxtv.org/hg/~pascoe/xc-test/)
cd xc-test
make
[sudo] make install
cd /lib/firmware
wget [http://www.linuxtv.org/downloads/firmware/dvb-usb-bluebird-01.fw](http://www.linuxtv.org/downloads/firmware/dvb-usb-bluebird-01.fw)
wget [http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/xc3028-dvico-au-01.fw](http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/xc3028-dvico-au-01.fw)
wget [http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/dvb-usb-bluebird-02.fw](http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/dvb-usb-bluebird-02.fw)

run me-tv!

cheers

---

### Post by Erlander on 2008-07-31
The newer versions of the linux kernel contain the bluebird firmware file.

Look in /lib/firmware/  and then the latest version (kernel) that you are using.

However it is sometimes necessary to copy the driver into /lib/firmware

One concern is that not all Dvico Fusion cards are the same.  [www.linuxtv.org](www.linuxtv.org) is the best spot to check this out.

I have used Mythtv but its a pain to setup.  As well as MeTv Kaffeine is worth trying too as its easy to configure and to scan for channels with.

Good luck.

Rob

---

### Post by Stolea on 2008-07-31
Thanks guys,
Will give it a go on the weekend and report back.
Cheers

---

### Post by mikeys749A on 2008-08-02
Does not work. My DVICo card is hooked up to cable and I am in California. None of the transponders in me-tv tune to the cable channels. The same card works perfectly in Win XP x64. I did all steps you listed OK except that the none of the "wget" worked. What do I do? Please advise.
I have DVICO Fusion HDTV Gold - PCI.This has been my biggest challenge. Also, my Logitech fusion webcam is no longer recognized under multimedia selector.



> **qhaz said:**
> . . . I share your pain.

Firstly you DON'T need Mythbuntu.  Simply install me-tv

[sudo] apt-get install me-tv

Apart from having to make your own channels.conf this program works just great.

To setup my DVICO stuff.
I can get it to work on my laptop using Hardy and kernel 2.6.24-19-generic by the following.

[sudo] apt-get install mercurial linux-headers-$(uname -r) build-essential 

hg clone [http://linuxtv.org/hg/~pascoe/xc-test/](http://linuxtv.org/hg/~pascoe/xc-test/)
cd xc-test
make
[sudo] make install
cd /lib/firmware
wget [http://www.linuxtv.org/downloads/firmware/dvb-usb-bluebird-01.fw](http://www.linuxtv.org/downloads/firmware/dvb-usb-bluebird-01.fw)
wget [http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/xc3028-dvico-au-01.fw](http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/xc3028-dvico-au-01.fw)
wget [http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/dvb-usb-bluebird-02.fw](http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/dvb-usb-bluebird-02.fw)

run me-tv!

cheers

---

### Post by Erlander on 2008-08-02
Mickey,

The cards being discussed in this thread are dvb as used in Europe and Australia.  Your North American ATSC card needs different solutions.

Try searching the forum or even a Google search.  From what I have seen on my brief search it should work out of the box.

Rob

---

### Post by Stolea on 2008-08-03
It all worked fine to this point:
```
peter@office:/lib/firmware$ wget http://www.linuxtv.org/downloads/fir...bluebird-01.fw
--17:44:17--  http://www.linuxtv.org/downloads/fir...bluebird-01.fw
           => `fir...bluebird-01.fw'
Resolving www.linuxtv.org... 212.227.166.180
Connecting to www.linuxtv.org|212.227.166.180|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
17:44:17 ERROR 404: Not Found.

peter@office:/lib/firmware$ wget http://www.itee.uq.edu.au/~chrisp/Li...dvico-au-01.fw
--17:44:35--  http://www.itee.uq.edu.au/~chrisp/Li...dvico-au-01.fw
           => `Li...dvico-au-01.fw'
Resolving www.itee.uq.edu.au... 130.102.79.1
Connecting to www.itee.uq.edu.au|130.102.79.1|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
17:44:35 ERROR 404: Not Found.

peter@office:/lib/firmware$ wget http://www.itee.uq.edu.au/~chrisp/Li...bluebird-02.fw
--17:45:18--  http://www.itee.uq.edu.au/~chrisp/Li...bluebird-02.fw
           => `Li...bluebird-02.fw'
Resolving www.itee.uq.edu.au... 130.102.79.1
Connecting to www.itee.uq.edu.au|130.102.79.1|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
17:45:19 ERROR 404: Not Found.

```
If I then open Me-TV and tell to set up the channels for Melbourne it can't find anything and of course won't start.
Whence shall we venture forth next??
Cheers

---

### Post by mikeys749A on 2008-08-03
Rob,

I've searched many,many times and find nothing. Can you help with finding solution for my card. Dvico refuse to provide driver for Linux. The card is recognized by Hardy x64, but do not know what to do from there. Please help. 

M





> **Erlander said:**
> Mickey,

The cards being discussed in this thread are dvb as used in Europe and Australia.  Your North American ATSC card needs different solutions.

Try searching the forum or even a Google search.  From what I have seen on my brief search it should work out of the box.

Rob

---

### Post by Erlander on 2008-08-03
In terminal enter "dmesg"

Amongst all the code you should find something like this:

```
 411.054015] usb 6-10: new high speed USB device using ehci_hcd and address 5
[  411.103032] usb 6-10: configuration #1 chosen from 1 choice
[  411.173435] dvb-usb: found a 'DViCO FusionHDTV DVB-T USB (TH7579)' in cold state, will try to load a firmware
[  411.191612] dvb-usb: downloading firmware from file 'dvb-usb-bluebird-01.fw'
[  411.218069] usbcore: registered new interface driver dvb_usb_cxusb
[  411.230187] usb 6-10: USB disconnect, address 5
[  411.230449] dvb-usb: generic DVB-USB module successfully deinitialized and disconnected.
[  411.890192] usb 6-10: new high speed USB device using ehci_hcd and address 6
[  411.939136] usb 6-10: configuration #1 chosen from 1 choice
[  411.939603] dvb-usb: found a 'DViCO FusionHDTV DVB-T USB (TH7579)' in warm state.
[  411.939730] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[  411.944172] DVB: registering new adapter (DViCO FusionHDTV DVB-T USB (TH7579))
[  411.985992] DVB: registering frontend 0 (Zarlink MT352 DVB-T)...
[  412.028489] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:13.5/usb6/6-10/input/input7
[  412.050002] dvb-usb: schedule remote query interval to 100 msecs.
[  412.050007] dvb-usb: DViCO FusionHDTV DVB-T USB (TH7579) successfully initialized and connected.

```

It may have other entries between the various entries and of course yours is pci not usb.

Hope this helps.

Rob

---

### Post by Erlander on 2008-08-03
> **mikeys749A said:**
> Rob,

I've searched many,many times and find nothing. Can you help with finding solution for my card. Dvico refuse to provide driver for Linux. The card is recognized by Hardy x64, but do not know what to do from there. Please help. 

M

Hi Mikey,

I'm not good on ATSC but will try.

First can you post the relevant part of your dmesg output?

In my experience if the card is recognised then all I have done is started Kaffeine or MeTv, scanned for channels and off it went.

Yes DVico don't provide linux drivers but support for most cards is built into linux and for those cards they pretty well work oput of the box.

Rob

---

### Post by crispyrob on 2008-08-03
Thanks for this info. One of the things I've been looking for is a basic dvb app. I've managed to get my dvico card working in Kaffeine but it was kind of clunky. To find out there's a dedicated dvb tv app with integrated recording scheduling is a real bonus. And it's an Aussie program to boot!

When I next get a chance to I'll download it and give it a go.

---

### Post by Stolea on 2008-08-03
This is what readout I get:```
   41.086064] gameport: EMU10K1 is pci0000:02:0b.1/gameport0, io 0xdfe0, speed 1046kHz
[   41.560395] Linux video capture interface: v2.00
[   41.867479] parport_pc 00:09: reported by Plug and Play ACPI
[   41.867604] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   41.919565] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   41.919651] ACPI: PCI Interrupt 0000:02:0c.0[A] -> GSI 20 (level, low) -> IRQ 21
[   41.919755] cx88[0]: subsystem: 18ac:db40, board: DViCO FusionHDTV DVB-T Hybrid [card=46,autodetected]
[   41.919763] cx88[0]: TV tuner type 72, Radio tuner type -1
[   41.938099] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.6 loaded
[   42.106734] cx88[0]/0: found at 0000:02:0c.0, rev: 5, irq: 21, latency: 64, mmio: 0xfb000000
[   42.205094] tuner 0-0061: chip found @ 0xc2 (cx88[0])
[   42.205129] tuner-simple 0-0061: type set to 72 (Thomson FE6600)
[   42.205134] tuner 0-0061: type set to Thomson FE6600
[   42.205139] tuner-simple 0-0061: type set to 72 (Thomson FE6600)
[   42.205144] tuner 0-0061: type set to Thomson FE6600
[   42.214735] cx88[0]/0: registered device video0 [v4l2]
[   42.214769] cx88[0]/0: registered device vbi0
[   42.224701] cx88[0]/2: cx2388x 8802 Driver Manager
[   42.224733] ACPI: PCI Interrupt 0000:02:0c.2[A] -> GSI 20 (level, low) -> IRQ 21
[   42.224747] cx88[0]/2: found at 0000:02:0c.2, rev: 5, irq: 21, latency: 64, mmio: 0xfd000000
[   42.409324] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[   42.409331] cx88/2: registering cx8802 driver, type: dvb access: shared
[   42.409338] cx88[0]/2: subsystem: 18ac:db40, board: DViCO FusionHDTV DVB-T Hybrid [card=46]
[   42.409344] cx88[0]/2: cx2388x based DVB/ATSC card
[   42.644945] DVB: registering new adapter (cx88[0])
[   42.644953] DVB: registering frontend 0 (Zarlink ZL10353 DVB-T)...
[   42.771107] cx2388x alsa driver version 0.0.6 loaded
[   42.771193] ACPI: PCI Interrupt 0000:02:0c.1[A] -> GSI 20 (level, low) -> IRQ 21
[   42.771233] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards

```
What now???

---

### Post by Stolea on 2008-08-03
Just as as an add-on to my previous post. I restarted the computer and now I get the following readout:
> [   38.533838] hiddev96hidraw1: USB HID v1.10 Device [DVICO DVICO USB HID Remocon V1.00] on usb-0000:00:1d.2-2
[   38.533866] usbcore: registered new interface driver usbhid
[   38.533872] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   38.653430] Linux video capture interface: v2.00
[   38.916581] iTCO_vendor_support: vendor-support=0
[   38.980438] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   38.980564] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0860)
[   38.980616] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   39.182284] usblp0: USB Bidirectional printer dev 6 if 0 alt 0 proto 2 vid 0x04A9 pid 0x10B7
[   39.182315] usbcore: registered new interface driver usblp
[   39.255723] intel_rng: FWH not detected
[   39.399461] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   39.399544] ACPI: PCI Interrupt 0000:02:0c.0[A] -> GSI 20 (level, low) -> IRQ 21
[   39.399634] cx88[0]: Your board has no valid PCI Subsystem ID and thus can't
[   39.399636] cx88[0]: be autodetected.  Please pass card=<n> insmod option to
[   39.399639] cx88[0]: workaround that.  Redirect complaints to the vendor of
[   39.399641] cx88[0]: the TV card.  Best regards,
[   39.399643] cx88[0]:         -- tux
[   39.399647] cx88[0]: Here is a list of valid choices for the card=<n> insmod option:
[   39.399651] cx88[0]:    card=0 -> UNKNOWN/GENERIC
[   39.399654] cx88[0]:    card=1 -> Hauppauge WinTV 34xxx models
[   39.399658] cx88[0]:    card=2 -> GDI Black Gold
[   39.399661] cx88[0]:    card=3 -> PixelView
[   39.399664] cx88[0]:    card=4 -> ATI TV Wonder Pro
[   39.399667] cx88[0]:    card=5 -> Leadtek Winfast 2000XP Expert
[   39.399671] cx88[0]:    card=6 -> AverTV Studio 303 (M126)
[   39.399674] cx88[0]:    card=7 -> MSI TV-@nywhere Master
[   39.399678] cx88[0]:    card=8 -> Leadtek Winfast DV2000
[   39.399681] cx88[0]:    card=9 -> Leadtek PVR 2000
[   39.399684] cx88[0]:    card=10 -> IODATA GV-VCP3/PCI
[   39.399688] cx88[0]:    card=11 -> Prolink PlayTV PVR
[   39.399691] cx88[0]:    card=12 -> ASUS PVR-416
[   39.399694] cx88[0]:    card=13 -> MSI TV-@nywhere
[   39.399697] cx88[0]:    card=14 -> KWorld/VStream XPert DVB-T
[   39.399701] cx88[0]:    card=15 -> DViCO FusionHDTV DVB-T1
[   39.399704] cx88[0]:    card=16 -> KWorld LTV883RF
[   39.399707] cx88[0]:    card=17 -> DViCO FusionHDTV 3 Gold-Q
[   39.399711] cx88[0]:    card=18 -> Hauppauge Nova-T DVB-T
[   39.399714] cx88[0]:    card=19 -> Conexant DVB-T reference design
[   39.399718] cx88[0]:    card=20 -> Provideo PV259
[   39.399721] cx88[0]:    card=21 -> DViCO FusionHDTV DVB-T Plus
[   39.399724] cx88[0]:    card=22 -> pcHDTV HD3000 HDTV
[   39.399728] cx88[0]:    card=23 -> digitalnow DNTV Live! DVB-T
[   39.399732] cx88[0]:    card=24 -> Hauppauge WinTV 28xxx (Roslyn) models
[   39.399735] cx88[0]:    card=25 -> Digital-Logic MICROSPACE Entertainment Center (MEC)
[   39.399739] cx88[0]:    card=26 -> IODATA GV/BCTV7E
[   39.399743] cx88[0]:    card=27 -> PixelView PlayTV Ultra Pro (Stereo)
[   39.399746] cx88[0]:    card=28 -> DViCO FusionHDTV 3 Gold-T
[   39.399750] cx88[0]:    card=29 -> ADS Tech Instant TV DVB-T PCI
[   39.399753] cx88[0]:    card=30 -> TerraTec Cinergy 1400 DVB-T
[   39.399757] cx88[0]:    card=31 -> DViCO FusionHDTV 5 Gold
[   39.399760] cx88[0]:    card=32 -> AverMedia UltraTV Media Center PCI 550
[   39.399764] cx88[0]:    card=33 -> Kworld V-Stream Xpert DVD
[   39.399767] cx88[0]:    card=34 -> ATI HDTV Wonder
[   39.399771] cx88[0]:    card=35 -> WinFast DTV1000-T
[   39.399774] cx88[0]:    card=36 -> AVerTV 303 (M126)
[   39.399777] cx88[0]:    card=37 -> Hauppauge Nova-S-Plus DVB-S
[   39.399781] cx88[0]:    card=38 -> Hauppauge Nova-SE2 DVB-S
[   39.399784] cx88[0]:    card=39 -> KWorld DVB-S 100
[   39.399787] cx88[0]:    card=40 -> Hauppauge WinTV-HVR1100 DVB-T/Hybrid
[   39.399791] cx88[0]:    card=41 -> Hauppauge WinTV-HVR1100 DVB-T/Hybrid (Low Profile)
[   39.399795] cx88[0]:    card=42 -> digitalnow DNTV Live! DVB-T Pro
[   39.399799] cx88[0]:    card=43 -> KWorld/VStream XPert DVB-T with cx22702
[   39.399802] cx88[0]:    card=44 -> DViCO FusionHDTV DVB-T Dual Digital
[   39.399806] cx88[0]:    card=45 -> KWorld HardwareMpegTV XPert
[   39.399809] cx88[0]:    card=46 -> DViCO FusionHDTV DVB-T Hybrid
[   39.399814] cx88[0]:    card=47 -> pcHDTV HD5500 HDTV
[   39.399817] cx88[0]:    card=48 -> Kworld MCE 200 Deluxe
[   39.399820] cx88[0]:    card=49 -> PixelView PlayTV P7000
[   39.399824] cx88[0]:    card=50 -> NPG Tech Real TV FM Top 10
[   39.399827] cx88[0]:    card=51 -> WinFast DTV2000 H
[   39.399830] cx88[0]:    card=52 -> Geniatech DVB-S
[   39.399834] cx88[0]:    card=53 -> Hauppauge WinTV-HVR3000 TriMode Analog/DVB-S/DVB-T
[   39.399838] cx88[0]:    card=54 -> Norwood Micro TV Tuner
[   39.399841] cx88[0]:    card=55 -> Shenzhen Tungsten Ages Tech TE-DTV-250 / Swann OEM
[   39.399845] cx88[0]:    card=56 -> Hauppauge WinTV-HVR1300 DVB-T/Hybrid MPEG Encoder
[   39.399850] cx88[0]:    card=57 -> ADS Tech Instant Video PCI
[   39.399853] cx88[0]:    card=58 -> DViCO FusionHDTV DVB-T PRO
[   39.399857] cx88[0]: subsystem: 0000:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
[   39.399862] cx88[0]: TV tuner type -1, Radio tuner type -1
[   39.447385] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   39.557437] cx88[0]/0: found at 0000:02:0c.0, rev: 5, irq: 21, latency: 64, mmio: 0xfd000000
[   39.984105] TEA5761 detected.
[   39.984113] tuner' 0-0010: chip found @ 0x20 (cx88[0])
[   39.986636] TEA5761 detected.
[   39.986641] tea5761 0-0010: type set to Philips TEA5761HN FM Radio
[   39.989810] tuner' 0-0042: chip found @ 0x84 (cx88[0])
[   39.989817] tda9887 0-0042: tda988[5/6/7] found @ 0x42 (tuner')
[   39.993423] tuner' 0-0043: chip found @ 0x86 (cx88[0])
[   39.993430] tda9887 0-0043: tda988[5/6/7] found @ 0x43 (tuner')
[   39.996101] tuner' 0-004a: chip found @ 0x94 (cx88[0])
[   39.996106] tda9887 0-004a: tda988[5/6/7] found @ 0x4a (tuner')
[   39.998763] tuner' 0-004b: chip found @ 0x96 (cx88[0])
[   39.998768] tda9887 0-004b: tda988[5/6/7] found @ 0x4b (tuner')
[   40.002969] All bytes are equal. It is not a TEA5767
[   40.002977] tuner' 0-0060: chip found @ 0xc0 (cx88[0])
[   40.003184] tuner' 0-0061: chip found @ 0xc2 (cx88[0])
[   40.003392] tuner' 0-0062: chip found @ 0xc4 (cx88[0])
[   40.003600] tuner' 0-0063: chip found @ 0xc6 (cx88[0])
[   40.003807] tuner' 0-0064: chip found @ 0xc8 (cx88[0])
[   40.004012] tuner' 0-0065: chip found @ 0xca (cx88[0])
[   40.004218] tuner' 0-0066: chip found @ 0xcc (cx88[0])
[   40.004424] tuner' 0-0067: chip found @ 0xce (cx88[0])
[   40.004629] tuner' 0-0068: chip found @ 0xd0 (cx88[0])
[   40.004836] tuner' 0-0069: chip found @ 0xd2 (cx88[0])
[   40.005044] tuner' 0-006a: chip found @ 0xd4 (cx88[0])
[   40.005253] tuner' 0-006c: chip found @ 0xd8 (cx88[0])
[   40.005462] tuner' 0-006d: chip found @ 0xda (cx88[0])
[   40.005669] tuner' 0-006e: chip found @ 0xdc (cx88[0])
[   40.006002] cx88[0]/0: registered device video0 [v4l2]
[   40.006035] cx88[0]/0: registered device vbi0
[   40.006049] tuner' 0-0060: tuner type not set

When I try to start MeTv I get the error message "No tuner device"

---

### Post by mikeys749A on 2008-08-03
Here is dmesg output:

[   34.606647]    groups: 03
[   34.606648] CPU1 attaching sched-domain:
[   34.606650]  domain 0: span 03
[   34.606651]   groups: 02 01
[   34.606653]   domain 1: span 03
[   34.606654]    groups: 03
[   34.606846] net_namespace: 120 bytes
[   34.607158] Time: 19:39:54  Date: 08/03/08
[   34.607179] NET: Registered protocol family 16
[   34.607346] ACPI: bus type pci registered
[   34.607409] PCI: Using configuration type 1
[   34.608576] ACPI: EC: Look up EC in DSDT
[   34.609888] ACPI: Interpreter enabled
[   34.609891] ACPI: (supports S0 S1 S3 S4 S5)
[   34.609904] ACPI: Using IOAPIC for interrupt routing
[   34.612904] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   34.614330] PCI: Transparent bridge - 0000:00:1e.0
[   34.614744] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   34.615038] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[   34.615182] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[   34.615273] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
[   34.615363] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX5._PRT]
[   34.618357] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[   34.618432] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12)
[   34.618504] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 *10 11 12)
[   34.618575] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *9 10 11 12)
[   34.618647] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[   34.618719] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11 12)
[   34.618790] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 *9 10 11 12)
[   34.618861] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 *11 12)
[   34.618965] Linux Plug and Play Support v0.97 (c) Adam Belay
[   34.618991] pnp: PnP ACPI init
[   34.618996] ACPI: bus type pnp registered
[   34.621142] pnp: PnP ACPI: found 12 devices
[   34.621144] ACPI: ACPI bus type pnp unregistered
[   34.621348] PCI: Using ACPI for IRQ routing
[   34.621350] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   34.634289] NET: Registered protocol family 8
[   34.634291] NET: Registered protocol family 20
[   34.634329] PCI-GART: No AMD northbridge found.
[   34.634364] AppArmor: AppArmor Filesystem Enabled
[   34.638258] Time: tsc clocksource has been installed.
[   34.646322] system 00:01: iomem range 0xf0000000-0xf3ffffff has been reserved
[   34.646326] system 00:01: iomem range 0xfed13000-0xfed13fff has been reserved
[   34.646329] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[   34.646332] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[   34.646335] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[   34.646339] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[   34.646342] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved
[   34.646345] system 00:01: iomem range 0xfed45000-0xfed99fff has been reserved
[   34.646348] system 00:01: iomem range 0xc0000-0xdffff has been reserved
[   34.646352] system 00:01: iomem range 0xe0000-0xfffff could not be reserved
[   34.646360] system 00:06: ioport range 0x500-0x53f has been reserved
[   34.646363] system 00:06: ioport range 0x400-0x47f has been reserved
[   34.646366] system 00:06: ioport range 0x680-0x6ff has been reserved
[   34.646764] PCI: Bridge: 0000:00:01.0
[   34.646766]   IO window: 3000-3fff
[   34.646769]   MEM window: e3400000-e34fffff
[   34.646771]   PREFETCH window: d0000000-dfffffff
[   34.646774] PCI: Bridge: 0000:00:1c.0
[   34.646775]   IO window: disabled.
[   34.646779]   MEM window: disabled.
[   34.646781]   PREFETCH window: disabled.
[   34.646785] PCI: Bridge: 0000:00:1c.4
[   34.646787]   IO window: 2000-2fff
[   34.646791]   MEM window: e3300000-e33fffff
[   34.646793]   PREFETCH window: e3600000-e36fffff
[   34.646797] PCI: Bridge: 0000:00:1c.5
[   34.646799]   IO window: 1000-1fff
[   34.646802]   MEM window: e3200000-e32fffff
[   34.646805]   PREFETCH window: disabled.
[   34.646809] PCI: Bridge: 0000:05:00.0
[   34.646810]   IO window: disabled.
[   34.646814]   MEM window: e3000000-e30fffff
[   34.646818]   PREFETCH window: disabled.
[   34.646822] PCI: Bridge: 0000:00:1e.0
[   34.646823]   IO window: disabled.
[   34.646826]   MEM window: e0000000-e31fffff
[   34.646829]   PREFETCH window: disabled.
[   34.646840] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   34.646844] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   34.646859] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[   34.646863] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   34.646877] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 17 (level, low) -> IRQ 17
[   34.646880] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   34.646894] ACPI: PCI Interrupt 0000:00:1c.5[B] -> GSI 16 (level, low) -> IRQ 16
[   34.646898] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   34.646906] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   34.646924] NET: Registered protocol family 2
[   34.682555] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   34.683600] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[   34.689083] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   34.689802] TCP: Hash tables configured (established 524288 bind 65536)
[   34.689804] TCP reno registered
[   34.698607] checking if image is initramfs... it is
[   35.145839] Switched to high resolution mode on CPU 1
[   35.149496] Switched to high resolution mode on CPU 0
[   35.333865] Freeing initrd memory: 7534k freed
[   35.337635] audit: initializing netlink socket (disabled)
[   35.337654] audit(1217792394.376:1): initialized
[   35.339557] VFS: Disk quotas dquot_6.5.1
[   35.339615] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   35.339717] io scheduler noop registered
[   35.339718] io scheduler anticipatory registered
[   35.339720] io scheduler deadline registered
[   35.339816] io scheduler cfq registered (default)
[   35.340901] Boot video device is 0000:01:00.0
[   35.343402] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   35.343429] assign_interrupt_mode Found MSI capability
[   35.343451] Allocate Port Service[0000:00:01.0:pcie00]
[   35.343515] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   35.343548] assign_interrupt_mode Found MSI capability
[   35.343575] Allocate Port Service[0000:00:1c.0:pcie00]
[   35.343603] Allocate Port Service[0000:00:1c.0:pcie02]
[   35.343669] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   35.343702] assign_interrupt_mode Found MSI capability
[   35.343729] Allocate Port Service[0000:00:1c.4:pcie00]
[   35.343757] Allocate Port Service[0000:00:1c.4:pcie02]
[   35.343825] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   35.343858] assign_interrupt_mode Found MSI capability
[   35.343885] Allocate Port Service[0000:00:1c.5:pcie00]
[   35.343912] Allocate Port Service[0000:00:1c.5:pcie02]
[   35.365362] Real Time Clock Driver v1.12ac
[   35.365447] Linux agpgart interface v0.102
[   35.365449] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   35.365565] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   35.366078] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   35.366702] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   35.366756] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   35.366833] PNP: PS/2 Controller [PNP0f03:PS2M] at 0x60,0x64 irq 12
[   35.366834] PNP: PS/2 controller doesn't have KBD irq; using default 1
[   35.369880] serio: i8042 KBD port at 0x60,0x64 irq 1
[   35.369884] serio: i8042 AUX port at 0x60,0x64 irq 12
[   35.380835] mice: PS/2 mouse device common for all mice
[   35.380875] cpuidle: using governor ladder
[   35.380877] cpuidle: using governor menu
[   35.381015] NET: Registered protocol family 1
[   35.381096] registered taskstats version 1
[   35.381217]   Magic number: 4:385:697
[   35.381296] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   35.381298] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   35.381299] EDD information not available.
[   35.381305] Freeing unused kernel memory: 320k freed
[   36.533290] fuse init (API version 7.9)
[   36.547547] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   36.547557] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   36.680903] usbcore: registered new interface driver usbfs
[   36.680923] usbcore: registered new interface driver hub
[   36.681164] usbcore: registered new device driver usb
[   36.688119] USB Universal Host Controller Interface driver v3.0
[   36.688169] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
[   36.688179] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   36.688182] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   36.688415] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   36.688443] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00004080
[   36.688561] usb usb1: configuration #1 chosen from 1 choice
[   36.688582] hub 1-0:1.0: USB hub found
[   36.688588] hub 1-0:1.0: 2 ports detected
[   36.763366] SCSI subsystem initialized
[   36.775990] libata version 3.00 loaded.
[   36.790345] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   36.790356] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   36.790359] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   36.790377] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   36.790402] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00004060
[   36.790489] usb usb2: configuration #1 chosen from 1 choice
[   36.790508] hub 2-0:1.0: USB hub found
[   36.790513] hub 2-0:1.0: 2 ports detected
[   36.802997] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
[   36.803000] Copyright (c) 1999-2006 Intel Corporation.
[   36.858422] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   36.882863] Floppy drive(s): fd0 is 1.44M
[   36.894083] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   36.894093] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   36.894096] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   36.894116] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   36.894139] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00004040
[   36.894230] usb usb3: configuration #1 chosen from 1 choice
[   36.894248] hub 3-0:1.0: USB hub found
[   36.894253] hub 3-0:1.0: 2 ports detected
[   36.901622] FDC 0 is a post-1991 82077
[   36.997860] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[   36.997871] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   36.997874] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   36.997898] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   36.997923] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00004020
[   36.998010] usb usb4: configuration #1 chosen from 1 choice
[   36.998027] hub 4-0:1.0: USB hub found
[   36.998032] hub 4-0:1.0: 2 ports detected
[   37.029208] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   37.101727] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
[   37.102180] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   37.102186] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   37.102227] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   37.106136] ehci_hcd 0000:00:1d.7: debug port 1
[   37.106140] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   37.106146] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xe3504400
[   37.156933] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   37.157032] usb usb5: configuration #1 chosen from 1 choice
[   37.157052] hub 5-0:1.0: USB hub found
[   37.157059] hub 5-0:1.0: 8 ports detected
[   37.260841] ACPI: PCI Interrupt 0000:06:08.2[C] -> GSI 23 (level, low) -> IRQ 23
[   37.261329] ehci_hcd 0000:06:08.2: EHCI Host Controller
[   37.261372] ehci_hcd 0000:06:08.2: new USB bus registered, assigned bus number 6
[   37.261407] ehci_hcd 0000:06:08.2: irq 23, io mem 0xe3006800
[   37.261781] ahci 0000:03:00.0: version 3.0
[   37.261797] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   37.262201] ahci 0000:03:00.0: controller can't do NCQ, turning off CAP_NCQ
[   37.262204] ahci 0000:03:00.0: MV_AHCI HACK: port_map 0 -> 0
[   37.262207] ahci 0000:03:00.0: nr_ports (5) and implemented port map (0xf) don't match, using nr_ports
[   37.262209] ahci 0000:03:00.0: forcing PORTS_IMPL to 0x1f
[   37.272715] ehci_hcd 0000:06:08.2: USB 2.0 started, EHCI 0.95, driver 10 Dec 2004
[   37.272836] usb usb6: configuration #1 chosen from 1 choice
[   37.272862] hub 6-0:1.0: USB hub found
[   37.272869] hub 6-0:1.0: 5 ports detected
[   37.552134] usb 1-1: device not accepting address 2, error -71
[   38.262673] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 5 ports 3 Gbps 0x1f impl SATA mode
[   38.262677] ahci 0000:03:00.0: flags: 64bit stag pmp slum part 
[   38.262683] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   38.263473] scsi0 : ahci
[   38.263522] scsi1 : ahci
[   38.263555] scsi2 : ahci
[   38.263589] scsi3 : ahci
[   38.263624] scsi4 : ahci
[   38.263647] ata1: SATA max UDMA/133 abar m1024@0xe3300000 port 0xe3300100 irq 16
[   38.263650] ata2: SATA max UDMA/133 abar m1024@0xe3300000 port 0xe3300180 irq 16
[   38.263652] ata3: SATA max UDMA/133 abar m1024@0xe3300000 port 0xe3300200 irq 16
[   38.263655] ata4: SATA max UDMA/133 abar m1024@0xe3300000 port 0xe3300280 irq 16
[   38.263658] ata5: SATA max UDMA/133 abar m1024@0xe3300000 port 0xe3300300 irq 16
[   38.470167] usb 5-4: new high speed USB device using ehci_hcd and address 4
[   38.582477] ata1: SATA link down (SStatus 0 SControl 300)
[   38.602825] usb 5-4: configuration #1 chosen from 1 choice
[   38.845393] usb 6-2: new high speed USB device using ehci_hcd and address 2
[   38.901803] ata2: SATA link down (SStatus 0 SControl 300)
[   39.122046] usb 6-2: configuration #1 chosen from 1 choice
[   39.221112] ata3: SATA link down (SStatus 0 SControl 300)
[   39.360307] usb 1-1: new low speed USB device using uhci_hcd and address 4
[   39.539725] usb 1-1: configuration #1 chosen from 1 choice
[   39.540478] ata4: SATA link down (SStatus 0 SControl 300)
[   39.779917] usb 1-2: new low speed USB device using uhci_hcd and address 5
[   39.859771] ata5: SATA link down (SStatus 0 SControl 0)
[   39.859870] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   39.859901] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   39.859912] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   39.859936] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   39.859955] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   39.859963] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[   39.860860] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   39.860870] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   39.918065] e1000: 0000:04:00.0: e1000_probe: (PCI Express:2.5Gb/s:Width x1) 00:19:d1:26:67:7b
[   39.975328] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   39.975638] ACPI: PCI Interrupt 0000:05:04.0[A] -> GSI 18 (level, low) -> IRQ 18
[   39.984791] usb 1-2: configuration #1 chosen from 1 choice
[   39.996617] usbcore: registered new interface driver hiddev
[   40.010883] input: BTC USB Multimedia Keyboard as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input1
[   40.025645] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[e3104000-e31047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   40.025907] ACPI: PCI Interrupt 0000:06:0c.0[A] -> GSI 21 (level, low) -> IRQ 21
[   40.075923] ohci1394: fw-host1: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[e3006000-e30067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   40.075999] ACPI: PCI Interrupt 0000:06:08.0[A] -> GSI 21 (level, low) -> IRQ 21
[   40.076413] ohci_hcd 0000:06:08.0: OHCI Host Controller
[   40.076463] ohci_hcd 0000:06:08.0: new USB bus registered, assigned bus number 7
[   40.076476] ohci_hcd 0000:06:08.0: irq 21, io mem 0xe3005000
[   40.079776] ata_piix 0000:00:1f.1: version 2.12
[   40.079792] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   40.079820] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   40.080207] scsi5 : ata_piix
[   40.080245] scsi6 : ata_piix
[   40.080642] ata6: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x40b0 irq 14
[   40.080644] ata7: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x40b8 irq 15
[   40.091678] input,hidraw0: USB HID v1.10 Keyboard [BTC USB Multimedia Keyboard] on usb-0000:00:1d.0-1
[   40.234993] input: BTC USB Multimedia Keyboard as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.1/input/input2
[   40.641098] usb usb7: configuration #1 chosen from 1 choice
[   40.641119] hub 7-0:1.0: USB hub found
[   40.641127] hub 7-0:1.0: 3 ports detected
[   40.642151] input,hiddev96,hidraw1: USB HID v1.10 Device [BTC USB Multimedia Keyboard] on usb-0000:00:1d.0-1
[   40.746224] ata6.00: ATAPI: SONY    CD-RW  CRX220E1, 6YS1, max UDMA/33
[   40.746238] ata6.01: ATAPI: ATAPI   DVD A  DH20A4H, QP53, max UDMA/66
[   40.746246] ata6.01: limited to UDMA/33 due to 40-wire cable
[   40.917316] ata6.00: configured for UDMA/33
[   41.019641] hiddev97hidraw2: USB HID v1.10 Device [APC Back-UPS ES 350 FW:823.B1a.D USB FW:B1a] on usb-0000:00:1d.0-2
[   41.019657] usbcore: registered new interface driver usbhid
[   41.019661] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   41.104896] ata6.01: configured for UDMA/33
[   41.104936] ata7: port disabled. ignoring.
[   41.109655] scsi 5:0:0:0: CD-ROM            SONY     CD-RW  CRX220E1  6YS1 PQ: 0 ANSI: 5
[   41.110966] scsi 5:0:1:0: CD-ROM            ATAPI    DVD A  DH20A4H   QP53 PQ: 0 ANSI: 5
[   41.111031] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   41.111052] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   41.111082] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   41.111340] scsi7 : ata_piix
[   41.111469] scsi8 : ata_piix
[   41.111553] ata8: SATA max UDMA/133 cmd 0x40c8 ctl 0x40e4 bmdma 0x40a0 irq 19
[   41.111555] ata9: SATA max UDMA/133 cmd 0x40c0 ctl 0x40e0 bmdma 0x40a8 irq 19
[   41.152616] ACPI: PCI Interrupt 0000:06:08.1[B] -> GSI 22 (level, low) -> IRQ 22
[   41.153099] ohci_hcd 0000:06:08.1: OHCI Host Controller
[   41.153144] ohci_hcd 0000:06:08.1: new USB bus registered, assigned bus number 8
[   41.153161] ohci_hcd 0000:06:08.1: irq 22, io mem 0xe3004000
[   41.308738] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0090270001bc9f84]
[   41.309220] ata8.00: ATA-7: ST3500630AS, 3.AAK, max UDMA/133
[   41.309223] ata8.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   41.344657] ieee1394: Host added: ID:BUS[1-00:1023]  GUID[005042b5c00df532]
[   41.375438] ata8.00: configured for UDMA/133
[   41.539184] scsi 7:0:0:0: Direct-Access     ATA      ST3500630AS      3.AA PQ: 0 ANSI: 5
[   41.717907] usb usb8: configuration #1 chosen from 1 choice
[   41.717928] hub 8-0:1.0: USB hub found
[   41.717935] hub 8-0:1.0: 2 ports detected
[   42.245448] Driver 'sd' needs updating - please use bus_type methods
[   42.245534] sd 7:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   42.245545] sd 7:0:0:0: [sda] Write Protect is off
[   42.245547] sd 7:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   42.245560] sd 7:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   42.245598] sd 7:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   42.245609] sd 7:0:0:0: [sda] Write Protect is off
[   42.245610] sd 7:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   42.245623] sd 7:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   42.245626]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   42.262886]  sda1 sda2 < sda5 >
[   42.284200] sd 7:0:0:0: [sda] Attached SCSI disk
[   42.287438] sr 5:0:0:0: Attached scsi generic sg0 type 5
[   42.287454] scsi 5:0:1:0: Attached scsi generic sg1 type 5
[   42.287470] sd 7:0:0:0: Attached scsi generic sg2 type 0
[   42.321135] sr0: scsi3-mmc drive: 70x/52x writer cd/rw xa/form2 cdda tray
[   42.321141] Uniform CD-ROM driver Revision: 3.20
[   42.321194] sr 5:0:0:0: Attached scsi CD-ROM sr0
[   42.328584] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   42.328622] sr 5:0:1:0: Attached scsi CD-ROM sr1
[   42.604934] Attempting manual resume
[   42.604937] swsusp: Resume From Partition 8:5
[   42.604938] PM: Checking swsusp image.
[   42.605094] PM: Resume from disk failed.
[   42.651128] kjournald starting.  Commit interval 5 seconds
[   42.651138] EXT3-fs: mounted filesystem with ordered data mode.
[   49.043246] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   49.077198] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   49.100465] parport_pc 00:08: reported by Plug and Play ACPI
[   49.100521] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   49.152332] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   49.191473] EDAC MC: Ver: 2.1.0 Jul 11 2008
[   49.263892] EDAC i82975x: ECC disabled on both channels.
[   49.384044] input: Power Button (FF) as /devices/virtual/input/input4
[   49.443053] ACPI: Power Button (FF) [PWRF]
[   49.443115] input: Sleep Button (CM) as /devices/virtual/input/input5
[   49.486945] ACPI: Sleep Button (CM) [SLPB]
[   49.661719] Linux video capture interface: v2.00
[   49.806528] logips2pp: Detected unknown logitech mouse model 74
[   49.862651] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   49.862714] ACPI: PCI Interrupt 0000:05:02.0[A] -> GSI 18 (level, low) -> IRQ 18
[   49.862744] cx88[0]: subsystem: 18ac:d500, board: DViCO FusionHDTV 5 Gold [card=31,autodetected]
[   49.862746] cx88[0]: TV tuner type 64, Radio tuner type -1
[   49.917557] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.6 loaded
[   50.021457] cx88[0]/0: found at 0000:05:02.0, rev: 5, irq: 18, latency: 32, mmio: 0xe2000000
[   50.292294] input: PS/2 Logitech Mouse as /devices/platform/i8042/serio1/input/input6
[   50.378884] tuner' 0-0043: chip found @ 0x86 (cx88[0])
[   50.378890] tda9887 0-0043: tda988[5/6/7] found @ 0x43 (tuner')
[   50.382011] cx88_alsa: disagrees about version of symbol cx88_core_put
[   50.382014] cx88_alsa: Unknown symbol cx88_core_put
[   50.382073] cx88_alsa: disagrees about version of symbol cx88_core_irq
[   50.382074] cx88_alsa: Unknown symbol cx88_core_irq
[   50.382103] cx88_alsa: disagrees about version of symbol cx88_core_get
[   50.382104] cx88_alsa: Unknown symbol cx88_core_get
[   50.382333] cx88_alsa: disagrees about version of symbol cx88_sram_channel_dump
[   50.382334] cx88_alsa: Unknown symbol cx88_sram_channel_dump
[   50.382363] cx88_alsa: disagrees about version of symbol cx88_sram_channel_setup
[   50.382365] cx88_alsa: Unknown symbol cx88_sram_channel_setup
[   50.382502] cx88_alsa: disagrees about version of symbol videobuf_to_dma
[   50.382504] cx88_alsa: Unknown symbol videobuf_to_dma
[   50.389840] tuner' 0-0061: chip found @ 0xc2 (cx88[0])
[   50.389866] tuner-simple 0-0061: type set to 64 (LG TDVS-H06xF)
[   50.445587] usblp0: USB Bidirectional printer dev 4 if 1 alt 0 proto 2 vid 0x03F0 pid 0x5B11
[   50.445606] usbcore: registered new interface driver usblp
[   50.470832] input: i2c IR (FusionHDTV) as /devices/virtual/input/input7
[   50.479756] uvcvideo: disagrees about version of symbol video_devdata
[   50.479759] uvcvideo: Unknown symbol video_devdata
[   50.479954] uvcvideo: disagrees about version of symbol video_unregister_device
[   50.479955] uvcvideo: Unknown symbol video_unregister_device
[   50.480018] uvcvideo: disagrees about version of symbol video_device_alloc
[   50.480020] uvcvideo: Unknown symbol video_device_alloc
[   50.480066] uvcvideo: disagrees about version of symbol video_register_device
[   50.480067] uvcvideo: Unknown symbol video_register_device
[   50.480192] uvcvideo: disagrees about version of symbol video_device_release
[   50.480194] uvcvideo: Unknown symbol video_device_release
[   50.524776] ir-kbd-i2c: i2c IR (FusionHDTV) detected at i2c-0/0-006b/ir0 [cx88[0]]
[   50.548679] isl1208 0-006f: chip found, driver version 0.2
[   50.548715] isl1208 0-006f: rtc core: registered isl1208 as rtc0
[   50.549628] cx88[0]/0: registered device video0 [v4l2]
[   50.549646] cx88[0]/0: registered device vbi0
[   50.551164] cx88[0]/2: cx2388x 8802 Driver Manager
[   50.551181] ACPI: PCI Interrupt 0000:05:02.2[A] -> GSI 18 (level, low) -> IRQ 18
[   50.551191] cx88[0]/2: found at 0000:05:02.2, rev: 5, irq: 18, latency: 32, mmio: 0xe0000000
[   50.551312] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   50.551739] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   50.554772] usbcore: registered new interface driver snd-usb-audio
[   50.598942] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[   50.598946] cx88/2: registering cx8802 driver, type: dvb access: shared
[   50.598949] cx88[0]/2: subsystem: 18ac:d500, board: DViCO FusionHDTV 5 Gold [card=31]
[   50.598951] cx88[0]/2: cx2388x based DVB/ATSC card
[   50.948333] DVB: registering new adapter (cx88[0])
[   50.948338] DVB: registering frontend 0 (LG Electronics LGDT3303 VSB/QAM Frontend)...
[   51.291021] lp0: using parport0 (interrupt-driven).
[   51.360913] Adding 11871992k swap on /dev/sda5.  Priority:-1 extents:1 across:11871992k
[   51.897923] EXT3 FS on sda1, internal journal
[   53.054505] ip_tables: (C) 2000-2006 Netfilter Core Team
[   53.082546] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   53.150657] NET: Registered protocol family 10
[   53.150862] lo: Disabled Privacy Extensions
[   53.165305] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   53.783189] No dock devices found.
[   54.532850] ppdev: user-space parallel port driver
[   54.741166] audit(1217792414.534:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5474 profile="/usr/sbin/cupsd" namespace="default"
[   56.193922] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX
[   56.193926] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
[   56.197200] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   56.202694] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   58.301171] [drm] Initialized drm 1.1.0 20060810
[   59.480819] NET: Registered protocol family 17
[   72.259358] eth0: no IPv6 routers present

Not sure what to do?? Can you look at the above and advise. Thank you so much for your help.

Mikeys749A

---

### Post by mikeys749A on 2008-08-03
Hi Rob,
Already tried Kaffeine and MeTv - no luck. MeTV cannot tune to anything - I am only connected to cable TV which caries HDTV channels. I do not have antenna for off-the-air channels, only cable TV connection into my DVICo Fusion HDTV Gold PCI card. Here is dmesg output:

[ 34.606647] groups: 03
[ 34.606648] CPU1 attaching sched-domain:
[ 34.606650] domain 0: span 03
[ 34.606651] groups: 02 01
[ 34.606653] domain 1: span 03
[ 34.606654] groups: 03
[ 34.606846] net_namespace: 120 bytes
[ 34.607158] Time: 19:39:54 Date: 08/03/08
[ 34.607179] NET: Registered protocol family 16
[ 34.607346] ACPI: bus type pci registered
[ 34.607409] PCI: Using configuration type 1
[ 34.608576] ACPI: EC: Look up EC in DSDT
[ 34.609888] ACPI: Interpreter enabled
[ 34.609891] ACPI: (supports S0 S1 S3 S4 S5)
[ 34.609904] ACPI: Using IOAPIC for interrupt routing
[ 34.612904] ACPI: PCI Root Bridge [PCI0] (0000:00)
[ 34.614330] PCI: Transparent bridge - 0000:00:1e.0
[ 34.614744] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[ 34.615038] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[ 34.615182] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[ 34.615273] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
[ 34.615363] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX5._PRT]
[ 34.618357] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[ 34.618432] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12)
[ 34.618504] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 *10 11 12)
[ 34.618575] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *9 10 11 12)
[ 34.618647] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[ 34.618719] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11 12)
[ 34.618790] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 *9 10 11 12)
[ 34.618861] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 *11 12)
[ 34.618965] Linux Plug and Play Support v0.97 (c) Adam Belay
[ 34.618991] pnp: PnP ACPI init
[ 34.618996] ACPI: bus type pnp registered
[ 34.621142] pnp: PnP ACPI: found 12 devices
[ 34.621144] ACPI: ACPI bus type pnp unregistered
[ 34.621348] PCI: Using ACPI for IRQ routing
[ 34.621350] PCI: If a device doesn't work, try "pci=routeirq". If it helps, post a report
[ 34.634289] NET: Registered protocol family 8
[ 34.634291] NET: Registered protocol family 20
[ 34.634329] PCI-GART: No AMD northbridge found.
[ 34.634364] AppArmor: AppArmor Filesystem Enabled
[ 34.638258] Time: tsc clocksource has been installed.
[ 34.646322] system 00:01: iomem range 0xf0000000-0xf3ffffff has been reserved
[ 34.646326] system 00:01: iomem range 0xfed13000-0xfed13fff has been reserved
[ 34.646329] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[ 34.646332] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[ 34.646335] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[ 34.646339] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[ 34.646342] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved
[ 34.646345] system 00:01: iomem range 0xfed45000-0xfed99fff has been reserved
[ 34.646348] system 00:01: iomem range 0xc0000-0xdffff has been reserved
[ 34.646352] system 00:01: iomem range 0xe0000-0xfffff could not be reserved
[ 34.646360] system 00:06: ioport range 0x500-0x53f has been reserved
[ 34.646363] system 00:06: ioport range 0x400-0x47f has been reserved
[ 34.646366] system 00:06: ioport range 0x680-0x6ff has been reserved
[ 34.646764] PCI: Bridge: 0000:00:01.0
[ 34.646766] IO window: 3000-3fff
[ 34.646769] MEM window: e3400000-e34fffff
[ 34.646771] PREFETCH window: d0000000-dfffffff
[ 34.646774] PCI: Bridge: 0000:00:1c.0
[ 34.646775] IO window: disabled.
[ 34.646779] MEM window: disabled.
[ 34.646781] PREFETCH window: disabled.
[ 34.646785] PCI: Bridge: 0000:00:1c.4
[ 34.646787] IO window: 2000-2fff
[ 34.646791] MEM window: e3300000-e33fffff
[ 34.646793] PREFETCH window: e3600000-e36fffff
[ 34.646797] PCI: Bridge: 0000:00:1c.5
[ 34.646799] IO window: 1000-1fff
[ 34.646802] MEM window: e3200000-e32fffff
[ 34.646805] PREFETCH window: disabled.
[ 34.646809] PCI: Bridge: 0000:05:00.0
[ 34.646810] IO window: disabled.
[ 34.646814] MEM window: e3000000-e30fffff
[ 34.646818] PREFETCH window: disabled.
[ 34.646822] PCI: Bridge: 0000:00:1e.0
[ 34.646823] IO window: disabled.
[ 34.646826] MEM window: e0000000-e31fffff
[ 34.646829] PREFETCH window: disabled.
[ 34.646840] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[ 34.646844] PCI: Setting latency timer of device 0000:00:01.0 to 64
[ 34.646859] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[ 34.646863] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[ 34.646877] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 17 (level, low) -> IRQ 17
[ 34.646880] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[ 34.646894] ACPI: PCI Interrupt 0000:00:1c.5[b] -> GSI 16 (level, low) -> IRQ 16
[ 34.646898] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[ 34.646906] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[ 34.646924] NET: Registered protocol family 2
[ 34.682555] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[ 34.683600] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[ 34.689083] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[ 34.689802] TCP: Hash tables configured (established 524288 bind 65536)
[ 34.689804] TCP reno registered
[ 34.698607] checking if image is initramfs... it is
[ 35.145839] Switched to high resolution mode on CPU 1
[ 35.149496] Switched to high resolution mode on CPU 0
[ 35.333865] Freeing initrd memory: 7534k freed
[ 35.337635] audit: initializing netlink socket (disabled)
[ 35.337654] audit(1217792394.376:1): initialized
[ 35.339557] VFS: Disk quotas dquot_6.5.1
[ 35.339615] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[ 35.339717] io scheduler noop registered
[ 35.339718] io scheduler anticipatory registered
[ 35.339720] io scheduler deadline registered
[ 35.339816] io scheduler cfq registered (default)
[ 35.340901] Boot video device is 0000:01:00.0
[ 35.343402] PCI: Setting latency timer of device 0000:00:01.0 to 64
[ 35.343429] assign_interrupt_mode Found MSI capability
[ 35.343451] Allocate Port Service[0000:00:01.0cie00]
[ 35.343515] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[ 35.343548] assign_interrupt_mode Found MSI capability
[ 35.343575] Allocate Port Service[0000:00:1c.0cie00]
[ 35.343603] Allocate Port Service[0000:00:1c.0cie02]
[ 35.343669] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[ 35.343702] assign_interrupt_mode Found MSI capability
[ 35.343729] Allocate Port Service[0000:00:1c.4cie00]
[ 35.343757] Allocate Port Service[0000:00:1c.4cie02]
[ 35.343825] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[ 35.343858] assign_interrupt_mode Found MSI capability
[ 35.343885] Allocate Port Service[0000:00:1c.5cie00]
[ 35.343912] Allocate Port Service[0000:00:1c.5cie02]
[ 35.365362] Real Time Clock Driver v1.12ac
[ 35.365447] Linux agpgart interface v0.102
[ 35.365449] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[ 35.365565] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 35.366078] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 35.366702] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[ 35.366756] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[ 35.366833] PNP: PS/2 Controller [PNP0f03:PS2M] at 0x60,0x64 irq 12
[ 35.366834] PNP: PS/2 controller doesn't have KBD irq; using default 1
[ 35.369880] serio: i8042 KBD port at 0x60,0x64 irq 1
[ 35.369884] serio: i8042 AUX port at 0x60,0x64 irq 12
[ 35.380835] mice: PS/2 mouse device common for all mice
[ 35.380875] cpuidle: using governor ladder
[ 35.380877] cpuidle: using governor menu
[ 35.381015] NET: Registered protocol family 1
[ 35.381096] registered taskstats version 1
[ 35.381217] Magic number: 4:385:697
[ 35.381296] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[ 35.381298] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[ 35.381299] EDD information not available.
[ 35.381305] Freeing unused kernel memory: 320k freed
[ 36.533290] fuse init (API version 7.9)
[ 36.547547] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[ 36.547557] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[ 36.680903] usbcore: registered new interface driver usbfs
[ 36.680923] usbcore: registered new interface driver hub
[ 36.681164] usbcore: registered new device driver usb
[ 36.688119] USB Universal Host Controller Interface driver v3.0
[ 36.688169] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
[ 36.688179] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[ 36.688182] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[ 36.688415] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[ 36.688443] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00004080
[ 36.688561] usb usb1: configuration #1 chosen from 1 choice
[ 36.688582] hub 1-0:1.0: USB hub found
[ 36.688588] hub 1-0:1.0: 2 ports detected
[ 36.763366] SCSI subsystem initialized
[ 36.775990] libata version 3.00 loaded.
[ 36.790345] ACPI: PCI Interrupt 0000:00:1d.1[b] -> GSI 19 (level, low) -> IRQ 19
[ 36.790356] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[ 36.790359] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[ 36.790377] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[ 36.790402] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00004060
[ 36.790489] usb usb2: configuration #1 chosen from 1 choice
[ 36.790508] hub 2-0:1.0: USB hub found
[ 36.790513] hub 2-0:1.0: 2 ports detected
[ 36.802997] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
[ 36.803000] Copyright (c) 1999-2006 Intel Corporation.
[ 36.858422] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[ 36.882863] Floppy drive(s): fd0 is 1.44M
[ 36.894083] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[ 36.894093] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[ 36.894096] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[ 36.894116] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[ 36.894139] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00004040
[ 36.894230] usb usb3: configuration #1 chosen from 1 choice
[ 36.894248] hub 3-0:1.0: USB hub found
[ 36.894253] hub 3-0:1.0: 2 ports detected
[ 36.901622] FDC 0 is a post-1991 82077
[ 36.997860] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[ 36.997871] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[ 36.997874] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[ 36.997898] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[ 36.997923] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00004020
[ 36.998010] usb usb4: configuration #1 chosen from 1 choice
[ 36.998027] hub 4-0:1.0: USB hub found
[ 36.998032] hub 4-0:1.0: 2 ports detected
[ 37.029208] usb 1-1: new low speed USB device using uhci_hcd and address 2
[ 37.101727] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
[ 37.102180] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[ 37.102186] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[ 37.102227] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[ 37.106136] ehci_hcd 0000:00:1d.7: debug port 1
[ 37.106140] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[ 37.106146] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xe3504400
[ 37.156933] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[ 37.157032] usb usb5: configuration #1 chosen from 1 choice
[ 37.157052] hub 5-0:1.0: USB hub found
[ 37.157059] hub 5-0:1.0: 8 ports detected
[ 37.260841] ACPI: PCI Interrupt 0000:06:08.2[C] -> GSI 23 (level, low) -> IRQ 23
[ 37.261329] ehci_hcd 0000:06:08.2: EHCI Host Controller
[ 37.261372] ehci_hcd 0000:06:08.2: new USB bus registered, assigned bus number 6
[ 37.261407] ehci_hcd 0000:06:08.2: irq 23, io mem 0xe3006800
[ 37.261781] ahci 0000:03:00.0: version 3.0
[ 37.261797] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[ 37.262201] ahci 0000:03:00.0: controller can't do NCQ, turning off CAP_NCQ
[ 37.262204] ahci 0000:03:00.0: MV_AHCI HACK: port_map 0 -> 0
[ 37.262207] ahci 0000:03:00.0: nr_ports (5) and implemented port map (0xf) don't match, using nr_ports
[ 37.262209] ahci 0000:03:00.0: forcing PORTS_IMPL to 0x1f
[ 37.272715] ehci_hcd 0000:06:08.2: USB 2.0 started, EHCI 0.95, driver 10 Dec 2004
[ 37.272836] usb usb6: configuration #1 chosen from 1 choice
[ 37.272862] hub 6-0:1.0: USB hub found
[ 37.272869] hub 6-0:1.0: 5 ports detected
[ 37.552134] usb 1-1: device not accepting address 2, error -71
[ 38.262673] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 5 ports 3 Gbps 0x1f impl SATA mode
[ 38.262677] ahci 0000:03:00.0: flags: 64bit stag pmp slum part
[ 38.262683] PCI: Setting latency timer of device 0000:03:00.0 to 64
[ 38.263473] scsi0 : ahci
[ 38.263522] scsi1 : ahci
[ 38.263555] scsi2 : ahci
[ 38.263589] scsi3 : ahci
[ 38.263624] scsi4 : ahci
[ 38.263647] ata1: SATA max UDMA/133 abar m1024@0xe3300000 port 0xe3300100 irq 16
[ 38.263650] ata2: SATA max UDMA/133 abar m1024@0xe3300000 port 0xe3300180 irq 16
[ 38.263652] ata3: SATA max UDMA/133 abar m1024@0xe3300000 port 0xe3300200 irq 16
[ 38.263655] ata4: SATA max UDMA/133 abar m1024@0xe3300000 port 0xe3300280 irq 16
[ 38.263658] ata5: SATA max UDMA/133 abar m1024@0xe3300000 port 0xe3300300 irq 16
[ 38.470167] usb 5-4: new high speed USB device using ehci_hcd and address 4
[ 38.582477] ata1: SATA link down (SStatus 0 SControl 300)
[ 38.602825] usb 5-4: configuration #1 chosen from 1 choice
[ 38.845393] usb 6-2: new high speed USB device using ehci_hcd and address 2
[ 38.901803] ata2: SATA link down (SStatus 0 SControl 300)
[ 39.122046] usb 6-2: configuration #1 chosen from 1 choice
[ 39.221112] ata3: SATA link down (SStatus 0 SControl 300)
[ 39.360307] usb 1-1: new low speed USB device using uhci_hcd and address 4
[ 39.539725] usb 1-1: configuration #1 chosen from 1 choice
[ 39.540478] ata4: SATA link down (SStatus 0 SControl 300)
[ 39.779917] usb 1-2: new low speed USB device using uhci_hcd and address 5
[ 39.859771] ata5: SATA link down (SStatus 0 SControl 0)
[ 39.859870] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[ 39.859901] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[ 39.859912] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[ 39.859936] ACPI: PCI Interrupt 0000:00:1f.2[b] -> GSI 19 (level, low) -> IRQ 19
[ 39.859955] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[ 39.859963] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[ 39.860860] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[ 39.860870] PCI: Setting latency timer of device 0000:04:00.0 to 64
[ 39.918065] e1000: 0000:04:00.0: e1000_probe: (PCI Express:2.5Gb/s:Width x1) 00:19:d1:26:67:7b
[ 39.975328] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[ 39.975638] ACPI: PCI Interrupt 0000:05:04.0[A] -> GSI 18 (level, low) -> IRQ 18
[ 39.984791] usb 1-2: configuration #1 chosen from 1 choice
[ 39.996617] usbcore: registered new interface driver hiddev
[ 40.010883] input: BTC USB Multimedia Keyboard as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input1
[ 40.025645] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18] MMIO=[e3104000-e31047ff] Max Packet=[2048] IR/IT contexts=[4/8]
[ 40.025907] ACPI: PCI Interrupt 0000:06:0c.0[A] -> GSI 21 (level, low) -> IRQ 21
[ 40.075923] ohci1394: fw-host1: OHCI-1394 1.1 (PCI): IRQ=[21] MMIO=[e3006000-e30067ff] Max Packet=[2048] IR/IT contexts=[4/8]
[ 40.075999] ACPI: PCI Interrupt 0000:06:08.0[A] -> GSI 21 (level, low) -> IRQ 21
[ 40.076413] ohci_hcd 0000:06:08.0: OHCI Host Controller
[ 40.076463] ohci_hcd 0000:06:08.0: new USB bus registered, assigned bus number 7
[ 40.076476] ohci_hcd 0000:06:08.0: irq 21, io mem 0xe3005000
[ 40.079776] ata_piix 0000:00:1f.1: version 2.12
[ 40.079792] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[ 40.079820] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[ 40.080207] scsi5 : ata_piix
[ 40.080245] scsi6 : ata_piix
[ 40.080642] ata6: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x40b0 irq 14
[ 40.080644] ata7: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x40b8 irq 15
[ 40.091678] input,hidraw0: USB HID v1.10 Keyboard [BTC USB Multimedia Keyboard] on usb-0000:00:1d.0-1
[ 40.234993] input: BTC USB Multimedia Keyboard as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.1/input/input2
[ 40.641098] usb usb7: configuration #1 chosen from 1 choice
[ 40.641119] hub 7-0:1.0: USB hub found
[ 40.641127] hub 7-0:1.0: 3 ports detected
[ 40.642151] input,hiddev96,hidraw1: USB HID v1.10 Device [BTC USB Multimedia Keyboard] on usb-0000:00:1d.0-1
[ 40.746224] ata6.00: ATAPI: SONY CD-RW CRX220E1, 6YS1, max UDMA/33
[ 40.746238] ata6.01: ATAPI: ATAPI DVD A DH20A4H, QP53, max UDMA/66
[ 40.746246] ata6.01: limited to UDMA/33 due to 40-wire cable
[ 40.917316] ata6.00: configured for UDMA/33
[ 41.019641] hiddev97hidraw2: USB HID v1.10 Device [APC Back-UPS ES 350 FW:823.B1a.D USB FW:B1a] on usb-0000:00:1d.0-2
[ 41.019657] usbcore: registered new interface driver usbhid
[ 41.019661] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[ 41.104896] ata6.01: configured for UDMA/33
[ 41.104936] ata7: port disabled. ignoring.
[ 41.109655] scsi 5:0:0:0: CD-ROM SONY CD-RW CRX220E1 6YS1 PQ: 0 ANSI: 5
[ 41.110966] scsi 5:0:1:0: CD-ROM ATAPI DVD A DH20A4H QP53 PQ: 0 ANSI: 5
[ 41.111031] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[ 41.111052] ACPI: PCI Interrupt 0000:00:1f.2[b] -> GSI 19 (level, low) -> IRQ 19
[ 41.111082] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[ 41.111340] scsi7 : ata_piix
[ 41.111469] scsi8 : ata_piix
[ 41.111553] ata8: SATA max UDMA/133 cmd 0x40c8 ctl 0x40e4 bmdma 0x40a0 irq 19
[ 41.111555] ata9: SATA max UDMA/133 cmd 0x40c0 ctl 0x40e0 bmdma 0x40a8 irq 19
[ 41.152616] ACPI: PCI Interrupt 0000:06:08.1[b] -> GSI 22 (level, low) -> IRQ 22
[ 41.153099] ohci_hcd 0000:06:08.1: OHCI Host Controller
[ 41.153144] ohci_hcd 0000:06:08.1: new USB bus registered, assigned bus number 8
[ 41.153161] ohci_hcd 0000:06:08.1: irq 22, io mem 0xe3004000
[ 41.308738] ieee1394: Host added: ID:BUS[0-00:1023] GUID[0090270001bc9f84]
[ 41.309220] ata8.00: ATA-7: ST3500630AS, 3.AAK, max UDMA/133
[ 41.309223] ata8.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[ 41.344657] ieee1394: Host added: ID:BUS[1-00:1023] GUID[005042b5c00df532]
[ 41.375438] ata8.00: configured for UDMA/133
[ 41.539184] scsi 7:0:0:0: Direct-Access ATA ST3500630AS 3.AA PQ: 0 ANSI: 5
[ 41.717907] usb usb8: configuration #1 chosen from 1 choice
[ 41.717928] hub 8-0:1.0: USB hub found
[ 41.717935] hub 8-0:1.0: 2 ports detected
[ 42.245448] Driver 'sd' needs updating - please use bus_type methods
[ 42.245534] sd 7:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[ 42.245545] sd 7:0:0:0: [sda] Write Protect is off
[ 42.245547] sd 7:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 42.245560] sd 7:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 42.245598] sd 7:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[ 42.245609] sd 7:0:0:0: [sda] Write Protect is off
[ 42.245610] sd 7:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 42.245623] sd 7:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 42.245626] sda:<4>Driver 'sr' needs updating - please use bus_type methods
[ 42.262886] sda1 sda2 < sda5 >
[ 42.284200] sd 7:0:0:0: [sda] Attached SCSI disk
[ 42.287438] sr 5:0:0:0: Attached scsi generic sg0 type 5
[ 42.287454] scsi 5:0:1:0: Attached scsi generic sg1 type 5
[ 42.287470] sd 7:0:0:0: Attached scsi generic sg2 type 0
[ 42.321135] sr0: scsi3-mmc drive: 70x/52x writer cd/rw xa/form2 cdda tray
[ 42.321141] Uniform CD-ROM driver Revision: 3.20
[ 42.321194] sr 5:0:0:0: Attached scsi CD-ROM sr0
[ 42.328584] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[ 42.328622] sr 5:0:1:0: Attached scsi CD-ROM sr1
[ 42.604934] Attempting manual resume
[ 42.604937] swsusp: Resume From Partition 8:5
[ 42.604938] PM: Checking swsusp image.
[ 42.605094] PM: Resume from disk failed.
[ 42.651128] kjournald starting. Commit interval 5 seconds
[ 42.651138] EXT3-fs: mounted filesystem with ordered data mode.
[ 49.043246] input: PC Speaker as /devices/platform/pcspkr/input/input3
[ 49.077198] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[ 49.100465] parport_pc 00:08: reported by Plug and Play ACPI
[ 49.100521] parport0: PC-style at 0x378 (0x77, irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[ 49.152332] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[ 49.191473] EDAC MC: Ver: 2.1.0 Jul 11 2008
[ 49.263892] EDAC i82975x: ECC disabled on both channels.
[ 49.384044] input: Power Button (FF) as /devices/virtual/input/input4
[ 49.443053] ACPI: Power Button (FF) [PWRF]
[ 49.443115] input: Sleep Button (CM) as /devices/virtual/input/input5
[ 49.486945] ACPI: Sleep Button (CM) [SLPB]
[ 49.661719] Linux video capture interface: v2.00
[ 49.806528] logips2pp: Detected unknown logitech mouse model 74
[ 49.862651] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[ 49.862714] ACPI: PCI Interrupt 0000:05:02.0[A] -> GSI 18 (level, low) -> IRQ 18
[ 49.862744] cx88[0]: subsystem: 18ac:d500, board: DViCO FusionHDTV 5 Gold [card=31,autodetected]
[ 49.862746] cx88[0]: TV tuner type 64, Radio tuner type -1
[ 49.917557] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.6 loaded
[ 50.021457] cx88[0]/0: found at 0000:05:02.0, rev: 5, irq: 18, latency: 32, mmio: 0xe2000000
[ 50.292294] input: PS/2 Logitech Mouse as /devices/platform/i8042/serio1/input/input6
[ 50.378884] tuner' 0-0043: chip found @ 0x86 (cx88[0])
[ 50.378890] tda9887 0-0043: tda988[5/6/7] found @ 0x43 (tuner')
[ 50.382011] cx88_alsa: disagrees about version of symbol cx88_core_put
[ 50.382014] cx88_alsa: Unknown symbol cx88_core_put
[ 50.382073] cx88_alsa: disagrees about version of symbol cx88_core_irq
[ 50.382074] cx88_alsa: Unknown symbol cx88_core_irq
[ 50.382103] cx88_alsa: disagrees about version of symbol cx88_core_get
[ 50.382104] cx88_alsa: Unknown symbol cx88_core_get
[ 50.382333] cx88_alsa: disagrees about version of symbol cx88_sram_channel_dump
[ 50.382334] cx88_alsa: Unknown symbol cx88_sram_channel_dump
[ 50.382363] cx88_alsa: disagrees about version of symbol cx88_sram_channel_setup
[ 50.382365] cx88_alsa: Unknown symbol cx88_sram_channel_setup
[ 50.382502] cx88_alsa: disagrees about version of symbol videobuf_to_dma
[ 50.382504] cx88_alsa: Unknown symbol videobuf_to_dma
[ 50.389840] tuner' 0-0061: chip found @ 0xc2 (cx88[0])
[ 50.389866] tuner-simple 0-0061: type set to 64 (LG TDVS-H06xF)
[ 50.445587] usblp0: USB Bidirectional printer dev 4 if 1 alt 0 proto 2 vid 0x03F0 pid 0x5B11
[ 50.445606] usbcore: registered new interface driver usblp
[ 50.470832] input: i2c IR (FusionHDTV) as /devices/virtual/input/input7
[ 50.479756] uvcvideo: disagrees about version of symbol video_devdata
[ 50.479759] uvcvideo: Unknown symbol video_devdata
[ 50.479954] uvcvideo: disagrees about version of symbol video_unregister_device
[ 50.479955] uvcvideo: Unknown symbol video_unregister_device
[ 50.480018] uvcvideo: disagrees about version of symbol video_device_alloc
[ 50.480020] uvcvideo: Unknown symbol video_device_alloc
[ 50.480066] uvcvideo: disagrees about version of symbol video_register_device
[ 50.480067] uvcvideo: Unknown symbol video_register_device
[ 50.480192] uvcvideo: disagrees about version of symbol video_device_release
[ 50.480194] uvcvideo: Unknown symbol video_device_release
[ 50.524776] ir-kbd-i2c: i2c IR (FusionHDTV) detected at i2c-0/0-006b/ir0 [cx88[0]]
[ 50.548679] isl1208 0-006f: chip found, driver version 0.2
[ 50.548715] isl1208 0-006f: rtc core: registered isl1208 as rtc0
[ 50.549628] cx88[0]/0: registered device video0 [v4l2]
[ 50.549646] cx88[0]/0: registered device vbi0
[ 50.551164] cx88[0]/2: cx2388x 8802 Driver Manager
[ 50.551181] ACPI: PCI Interrupt 0000:05:02.2[A] -> GSI 18 (level, low) -> IRQ 18
[ 50.551191] cx88[0]/2: found at 0000:05:02.2, rev: 5, irq: 18, latency: 32, mmio: 0xe0000000
[ 50.551312] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[ 50.551739] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[ 50.554772] usbcore: registered new interface driver snd-usb-audio
[ 50.598942] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[ 50.598946] cx88/2: registering cx8802 driver, type: dvb access: shared
[ 50.598949] cx88[0]/2: subsystem: 18ac:d500, board: DViCO FusionHDTV 5 Gold [card=31]
[ 50.598951] cx88[0]/2: cx2388x based DVB/ATSC card
[ 50.948333] DVB: registering new adapter (cx88[0])
[ 50.948338] DVB: registering frontend 0 (LG Electronics LGDT3303 VSB/QAM Frontend)...
[ 51.291021] lp0: using parport0 (interrupt-driven).
[ 51.360913] Adding 11871992k swap on /dev/sda5. Priority:-1 extents:1 across:11871992k
[ 51.897923] EXT3 FS on sda1, internal journal
[ 53.054505] ip_tables: (C) 2000-2006 Netfilter Core Team
[ 53.082546] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[ 53.150657] NET: Registered protocol family 10
[ 53.150862] lo: Disabled Privacy Extensions
[ 53.165305] ip6_tables: (C) 2000-2006 Netfilter Core Team
[ 53.783189] No dock devices found.
[ 54.532850] ppdev: user-space parallel port driver
[ 54.741166] audit(1217792414.534:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5474 profile="/usr/sbin/cupsd" namespace="default"
[ 56.193922] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX
[ 56.193926] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
[ 56.197200] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 56.202694] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 58.301171] [drm] Initialized drm 1.1.0 20060810
[ 59.480819] NET: Registered protocol family 17
[ 72.259358] eth0: no IPv6 routers present

Not sure what to do?? Can you look at the above and advise. Thank you so much for your help.

Mikeys749A

> **Erlander said:**
> Hi Mikey,

I'm not good on ATSC but will try.

First can you post the relevant part of your dmesg output?

In my experience if the card is recognised then all I have done is started Kaffeine or MeTv, scanned for channels and off it went.

Yes DVico don't provide linux drivers but support for most cards is built into linux and for those cards they pretty well work oput of the box.

Rob

---

### Post by xc3RnbFO8P on 2008-08-03
Mikeys749A, Reinstall Hardy Heron.
Your card **DViCO FusionHDTV 5 Gold**
is supported by the kernel.
[http://www.linuxtv.org/wiki/index.php/DViCO_FusionHDTV5_USB_Gold]("http://www.linuxtv.org/wiki/index.php/DViCO_FusionHDTV5_USB_Gold")
All this is included:
>  - lgdt330x.ko
 - dvb-usb.ko
 - dvb-usb-cxusb.ko
It also requires the firmware file:
- dvb-usb-bluebird-01.fw
Just install Me-TV or Kaffeine.

PS. edit your post, go advance and use **#**

---

### Post by mikeys749A on 2008-08-03
Hi Ringi,

(1) Where do I get these drivers and firmware patch from? How do I install?

(2) I have reinstalled several times Hardy x64 and installed kaffeine and Me-TV, but nothing works after the fresh re-install. In kaffeine - cannot scan for any channels. In Me-TV - cannot tune to any transponder frequencies - tried all of them. Something is missing from the re-install setup. May be if I could find and install these drivers and firmware, wi is going to work??

Please advise.

Mikeys749A


> **Ringi said:**
> Mikeys749A, Reinstall Hardy Heron.
Your card **DViCO FusionHDTV 5 Gold**
is supported by the kernel.
[http://www.linuxtv.org/wiki/index.php/DViCO_FusionHDTV5_USB_Gold]("http://www.linuxtv.org/wiki/index.php/DViCO_FusionHDTV5_USB_Gold")
All this is included:

Just install Me-TV or Kaffeine.

PS. edit your post, go advance and use **#**

---

### Post by xc3RnbFO8P on 2008-08-03
> (1) Where do I get these drivers and firmware patch from? How do I install?
You don't have to install any drivers or firmware.
Try now to install Kaffeine,
see if you can scan channels.
If it doesnt work, reinstall Hardy 32 bit.
It is easer to get things working in 32 bit.

---

### Post by mikeys749A on 2008-08-03
The "start scan" button in kaffeine does not produce any channels - it has always been like that in 32-bit and in 64-bit. Something is missing, but what??? I have attached a screenshot of kaffeine setup. I have tried 32-bit hardy several times - same problem, dvico does not work.



> **Ringi said:**
> You don't have to install any drivers or firmware.
Try now to install Kaffeine,
see if you can scan channels.
If it doesnt work, reinstall Hardy 32 bit.
It is easer to get things working in 32 bit.

---

### Post by mikeys749A on 2008-08-03
See my response posted under you in the thread with a screenshot (png) of kaffeine setup.


> **Ringi said:**
> You don't have to install any drivers or firmware.
Try now to install Kaffeine,
see if you can scan channels.
If it doesnt work, reinstall Hardy 32 bit.
It is easer to get things working in 32 bit.

---

### Post by xc3RnbFO8P on 2008-08-03
> See my response posted under you in the thread with a screenshot (png) of kaffeine setup.
It is OK, first in Synaptic Package Manager:
> Settings> repositories> Ubuntu Software check all
Settings> repositories> Update> check all
Then install the codec from here (64 bit):
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by mikeys749A on 2008-08-03
The first thing I do after re-install is to install all Medibuntu codecs. Already done. I checked the other settings in repositories and now have 63 updates coming in. Will these updates help?? Ubuntu does not recommend these additional repositories in general as they are not supported and might damage your system, right? That's why I had left them unchecked.




> **Ringi said:**
> It is OK, first in Synaptic Package Manager:

Then install the codec from here (64 bit):
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by xc3RnbFO8P on 2008-08-03
> Ubuntu does not recommend these additional repositories in general as they are not supported and might damage your system, right? That's why I had left them unchecked.
You need this if want to play restricted formats, no worry.

---

### Post by mikeys749A on 2008-08-03
Nothing worked after updates. Here is terminal message for Me-TV when I try to run Me-TV from terminal:
Me TV-Message: 08/03/2008 15:43:38 - Me TV Version: 0.5.17
Me TV-Message: 08/03/2008 15:43:38 - Loading glade file '/usr/share/me-tv/glade/me-tv.glade'
Me TV-Message: 08/03/2008 15:43:38 - Creating EPG file at '/home/mikeys/.me-tv/epg.xml'
Me TV-Message: 08/03/2008 15:43:38 - EPG file loaded
Me TV-Message: 08/03/2008 15:43:38 - Channel file loaded

(me-tv:6771): Me TV-CRITICAL **: Exception message: 'There are no usable channels in the channels.conf file.'
Me TV-Message: 08/03/2008 15:43:38 - Exception in void Application::init(): There are no usable channels in the channels.conf file.
Me TV-Message: 08/03/2008 15:43:41 - Terminating application normally

Kaffeine does not scan either. Do not know what is missing.




> **Ringi said:**
> You need this if want to play restricted formats, no worry.

---

### Post by mikeys749A on 2008-08-03
see screenshot attached.


> **Ringi said:**
> You need this if want to play restricted formats, no worry.

---

### Post by xc3RnbFO8P on 2008-08-03
What kind of antenna do you use,
are you sure that you got clear
view to the transmitter?

---

### Post by mikeys749A on 2008-08-03
No antenna. I only have cable TV connection which carries HDTV channels. Same setup under Win XP x64 works perfectly - can get analog and digital channels from cable tv provider. 


> **Ringi said:**
> What kind of antenna do you use,
are you sure that you got clear
view to the transmitter?

---

### Post by xc3RnbFO8P on 2008-08-03
> There are no usable channels in the channels.conf file
In /home/your folder/.me-tv/channels.conf
show the output of channels.conf

---

### Post by mikeys749A on 2008-08-03
No ".me-tv" folder found. It is certainly not in my home/mikeys/ directory. ??? When I start Me-TV, I only get the following message: There are no usable channels in the channels.conf file. No option to scan. Where exactly can I find this channels.conf file??



> **Ringi said:**
> In /home/your folder/.me-tv/channels.conf
show the output of channels.conf

---

### Post by xc3RnbFO8P on 2008-08-03
> Where exactly can I find this channels.conf file??
It should be in /home/mikeys/.me-tv
**.me-tv** is a hiden folder
In file manager View> Show Hidden Files

---

### Post by mikeys749A on 2008-08-03
Channels.conf file is empty. Now what??



> **Ringi said:**
> It should be in /home/mikeys/.me-tv
**.me-tv** is a hiden folder
In file manager View> Show Hidden Files

---

### Post by xc3RnbFO8P on 2008-08-03
Contact your cable tv provider 
and get information about the Channels
or Google it.
The ATSC channels should look something like this:
> KNTV-HD :207000000:QAM_256:65:68:4
NBC Wea :207000000:QAM_256:81:84:5
KBWB-HD :503000000:QAM_256:49:52:3
KBWB-SD :503000000:QAM_256:65:68:4
KGO-DT :533000000:QAM_256:49:52:3
KGO-DT :533000000:QAM_256:65:68:4
KTSF-D2:551000000:QAM_256:49:68:4
If got this iformation from your provider,
you can add them by:
> sudo gedit /home/mikeys/.me-tv/channels.conf
copy/paste into the file and save.

---

### Post by mikeys749A on 2008-08-03
Will try it and let you know. Thanks so much.


> **Ringi said:**
> Contact your cable tv provider 
and get information about the Channels
or Google it.
The ATSC channels should look something like this:

If got this iformation from your provider,
you can add them by:

copy/paste into the file and save.

---

### Post by Stolea on 2008-08-04
Hi guys,
I am still no closer to getting my card to work.
I had a look at the [www.linuxtv.org](www.linuxtv.org) but it doesn't list anything for Dvico DVB-T Hybrid. The Hardy kernel seems to recognize the card (well most times at least) and the problem seems to stem from where I enter the wget commands (see my previous post in this thread).
Any suggestions?
Cheers

---

### Post by xc3RnbFO8P on 2008-08-04
Try to download the drivers from here:
[https://help.ubuntu.com/community/DViCO_Dual_Digital_4]("https://help.ubuntu.com/community/DViCO_Dual_Digital_4")

---

### Post by crispyrob on 2008-08-05
Hi Guys,
   I've downloaded me-tv from the Ubuntu repositories (me-tv 0.5.17). However, it just worked for me, so I can't offer any suggestions as to how you might be able to get your install going.

Once I started it up, it asked for my location (au-Adelaide), scanned for channels and found them, apart from some "failed to tune transponder at nnnnnn" messages. I'm not sure what these mean as all the local TV channels were found. Was able to watch SD and HD TV and the EPG was populated (something that the supplied WinXP software doesn't do!)

Tried on 2 versions of Ubuntu:
8.04 32 bit - custom spin provided by an Australian computer mag
8.04.1 64 bit (my main install)
Both on AMD64 dual core HW w 1GB ram, Nvidia 6600GT video
Dvico Fusion HDTV single tuner PCI card ~2 years old

I have installed restricted codecs to get mpeg/xvid/mp3 etc, but can't remember the exact package I downloaded

Screenshots here:
[http://picasaweb.google.com/rlacina/Linux_ScreenShots](http://picasaweb.google.com/rlacina/Linux_ScreenShots)

Rob.

---

### Post by xc3RnbFO8P on 2008-08-05
Can you show the subsystem ID.
In Terminal **lspci**

---

### Post by crispyrob on 2008-08-06
> **Ringi said:**
> Can you show the subsystem ID.
In Terminal **lspci**
Hi Ringi, not sure if your last post was directed at me, but here's the ouput of lspci:

00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev a2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 Communication controller: Agere Systems 56k WinModem (rev 01)
01:08.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
01:08.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
01:0a.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 01)
05:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)

lspci -v, gives the following info about the Dvico card:

01:08.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
	Subsystem: DViCO Corporation Unknown device db10
	Flags: bus master, medium devsel, latency 32, IRQ 21
	Memory at f0000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: [44] Vital Product Data
	Capabilities: [4c] Power Management version 2

01:08.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
	Subsystem: DViCO Corporation DVICO FusionHDTV DVB-T Plus
	Flags: bus master, medium devsel, latency 32, IRQ 21
	Memory at f1000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: [4c] Power Management version 2

---

### Post by xc3RnbFO8P on 2008-08-07
> Hi Ringi, not sure if your last post was directed at me, but here's the ouput of lspci:

yes and add to your list **lspci -vn**

---

### Post by crispyrob on 2008-08-08
> **Ringi said:**
> yes and add to your list **lspci -vn**
Sorry this has taken so long, but I've been doing some shift work this week and been trying to catch up on missed sleep as well as trying to keep up with normal family life...

Anyway, output of lspci -vn (just ths Dvico stuff):

Just curious as to what you hope to get from this info? To me it doesn't look like it shows you anything that's configurable anywhere.

01:08.0 0400: 14f1:8800 (rev 05)
	Subsystem: 18ac:db10
	Flags: bus master, medium devsel, latency 32, IRQ 21
	Memory at f0000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: [44] Vital Product Data
	Capabilities: [4c] Power Management version 2

01:08.2 0480: 14f1:8802 (rev 05)
	Subsystem: 18ac:db10
	Flags: bus master, medium devsel, latency 32, IRQ 21
	Memory at f1000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: [4c] Power Management version 2

---

### Post by xc3RnbFO8P on 2008-08-09
> Just curious as to what you hope to get from this info? To me it doesn't look like it shows you anything that's configurable anywhere.
It show which card is working out of the box.
It will help people to find out what to do.
lspci -vn 
Subsystem: 18ac:db10 
Just install Kaffeine or Me-tv.

---

### Post by Stolea on 2008-08-09
I still can't get my card to work. At least now I have a /dev/dvb/adapter0 directory. 
When I type ```
ls -l /dev/dvb/adapter0 
```
I get
```
peter@office:~$ ls -l /dev/dvb/adapter0 
total 0
crw-rw----+ 1 root video 212, 4 2008-08-09 18:22 demux0
crw-rw----+ 1 root video 212, 5 2008-08-09 18:22 dvr0
crw-rw----+ 1 root video 212, 3 2008-08-09 18:22 frontend0
crw-rw----+ 1 root video 212, 7 2008-08-09 18:22 net0

```
When I start MeTV and tell it configure the channels for Melbourne it tells me that it fails to tune to transponder 1234xxxx and goes through a list of failed tunes. Kaffeine scans but can't find anything. This card works just fine in WinXp, so there is no hardware problem.
I am just about to give up on this project. Any helpful suggestions, anyone??

---

### Post by xc3RnbFO8P on 2008-08-09
Stolea, did you install the drivers from here:
[https://help.ubuntu.com/community/DViCO_Dual_Digital_4]("https://help.ubuntu.com/community/DViCO_Dual_Digital_4")

---

### Post by Stolea on 2008-08-09
Ringi,
Yep, followed it and at least now my system recognizes the card (most of the time). Its a Dvico FusionHDTV DVB-T Hybrid (means its got an FM receiver inbuilt). Unfortunately I can't get it to tune to any of the channels.:(
Something interesting I discovered along the way is that if you install firmware (wget....)you have to actually shutdown and restart if you want to have the card functional in WinXp. Plain reboot will have WinXp throwing tantrums with the card.

---

### Post by gkasinath on 2008-08-19
Hey all, 

I am still fighting a battle with Ubuntu Gutsy and the Fusion DVB T Hybrid down here. 
Upon booting, the card is sometimes recognized and most times not. When it is recognized, I try to tune with MythTV and I cant get a lock on any signal. I learnt that it was a possible bug.. but since I read about me-tv form of scanning, the card aint playing ball.. kernel has not recognized it so far.. 

Is there something I am missing? Can someone please advise? 

Thanks
Gautham

---

### Post by mikeys749A on 2008-08-31
My cable provider refuses to provide QAM addresses for the free (nonencrypted) ATSC channels. There must be a way to scan for these channels. I tried with w_scan, but nothing happened. Under Win XP x64, the DVICO software scans and does all perfectly. I understand that this Korean manufacturer does not care about Linux users, so there is not software. IS THERE ANY WAY TO SCAN FOR THE ATSC or even regular CABLE CHANNELS?? Please advise. This is extremely frustrating.




> **Ringi said:**
> Contact your cable tv provider 
and get information about the Channels
or Google it.
The ATSC channels should look something like this:

If got this iformation from your provider,
you can add them by:

copy/paste into the file and save.

---

### Post by noigmn on 2008-09-11
Has anyone had any luck getting a hybrid to work in Australia on Hardy?

I've never had it work with anything beyond edgy on my dvico fusion hybrid.  I think module in the kernel is somehow incompatible or corrupted.  I even tried reinstalling the kernel with new settings and patches on Hardy but in the end gave up and reinstalled edgy.  My mythTV computer is dedicated to be purely TV and web search so it isn't the biggest problem, but still it would be nice to use the newer versions and features.  

Compatibility over the network with my macbook frontend is a big problem with the older version of myth also.

---

### Post by Pro-reason on 2008-09-28
> **Stolea said:**
> Ringi,
Yep, followed it and at least now my system recognizes the card (most of the time). Its a Dvico FusionHDTV DVB-T Hybrid (means its got an FM receiver inbuilt). Unfortunately I can't get it to tune to any of the channels.:(
Something interesting I discovered along the way is that if you install firmware (wget....)you have to actually shutdown and restart if you want to have the card functional in WinXp. Plain reboot will have WinXp throwing tantrums with the card.

By running this command, I can generate a file with the necessary frequencies for the channels:

```

scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/au-Melbourne > ~/.me-tv/channels.conf

```

Unfortunately, I can only get SBS:

```

SBS HD:536625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:102:103:784
SBS:536625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:161:81:785
SBS NEWS:536625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:162:83:786
SBS 2:536625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:161:81:787
SBS RADIO 1:536625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:0:201:798
SBS RADIO 2:536625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:0:202:799
SBS HD:536500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:102:103:784
SBS:536500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:161:81:785
SBS NEWS:536500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:162:83:786
SBS 2:536500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:161:81:787
SBS RADIO 1:536500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:0:201:798
SBS RADIO 2:536500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:0:202:799

```

On Windows, I can get other channels.  Has anyone had any luck getting this working for Melbourne?

---

### Post by slick1a on 2008-09-28
had pretty much the same as STOLEA originally :

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libaccess-bridge-java
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  dvb-utils libgnet2.0-0
The following NEW packages will be installed
  dvb-utils libgnet2.0-0 me-tv
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 441kB of archives.
After this operation, 3965kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main libgnet2.0-0 2.0.7-1build1 [115kB]
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe dvb-utils 1.1.1-3 [139kB]
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe me-tv 0.5.17-1 [187kB]
Fetched 441kB in 0s (462kB/s)
Selecting previously deselected package libgnet2.0-0.
(Reading database ... 134239 files and directories currently installed.)
Unpacking libgnet2.0-0 (from .../libgnet2.0-0_2.0.7-1build1_i386.deb) ...
Selecting previously deselected package dvb-utils.
Unpacking dvb-utils (from .../dvb-utils_1.1.1-3_i386.deb) ...
Selecting previously deselected package me-tv.
Unpacking me-tv (from .../me-tv_0.5.17-1_i386.deb) ...
Setting up libgnet2.0-0 (2.0.7-1build1) ...

Setting up dvb-utils (1.1.1-3) ...
udev active, devices will be created in /dev/.static/dev/

Setting up me-tv (0.5.17-1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
slick@slick-desktop:~$ sudo apt-get install mercurial linux-headers-$
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-$
slick@slick-desktop:~$ sudo apt-get install mercurial linux-headers-$ slick-r build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-$
slick@slick-desktop:~$ sudo hg clone [http://linuxtv.org/hg/~pascoe/xc-test/](http://linuxtv.org/hg/~pascoe/xc-test/)
sudo: hg: command not found
slick@slick-desktop:~$ cd xc-test
bash: cd: xc-test: No such file or directory
slick@slick-desktop:~$ makehg clone [http://linuxtv.org/hg/~pascoe/xc-test/](http://linuxtv.org/hg/~pascoe/xc-test/)
bash: makehg: command not found
slick@slick-desktop:~$ cd xc-test
bash: cd: xc-test: No such file or directory
slick@slick-desktop:~$ make install
make: *** No rule to make target `install'. Stop.
slick@slick-desktop:~$ cd /lib/firmware
slick@slick-desktop:/lib/firmware$ wget [http://www.linuxtv.org/downloads/fir...bluebird-01.fw](http://www.linuxtv.org/downloads/fir...bluebird-01.fw)
--15:17:44--  [http://www.linuxtv.org/downloads/fir...bluebird-01.fw](http://www.linuxtv.org/downloads/fir...bluebird-01.fw)
           => `fir...bluebird-01.fw'
Resolving [www.linuxtv.org](www.linuxtv.org)... 212.227.166.180
Connecting to [www.linuxtv.org|212.227.166.180|:80](www.linuxtv.org|212.227.166.180|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
15:17:44 ERROR 404: Not Found.

slick@slick-desktop:/lib/firmware$ wget [http://www.itee.uq.edu.au/~chrisp/Li...dvico-au-01.fw](http://www.itee.uq.edu.au/~chrisp/Li...dvico-au-01.fw)
--15:17:44--  [http://www.itee.uq.edu.au/~chrisp/Li...dvico-au-01.fw](http://www.itee.uq.edu.au/~chrisp/Li...dvico-au-01.fw)
           => `Li...dvico-au-01.fw'
Resolving [www.itee.uq.edu.au](www.itee.uq.edu.au)... 130.102.79.1
Connecting to [www.itee.uq.edu.au|130.102.79.1|:80](www.itee.uq.edu.au|130.102.79.1|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
15:17:46 ERROR 404: Not Found.

slick@slick-desktop:/lib/firmware$ wget [http://www.itee.uq.edu.au/~chrisp/Li...bluebird-02.fw--15:18:34--](http://www.itee.uq.edu.au/~chrisp/Li...bluebird-02.fw--15:18:34--)  [http://www.itee.uq.edu.au/~chrisp/Li...bluebird-02.fw](http://www.itee.uq.edu.au/~chrisp/Li...bluebird-02.fw)
           => `Li...bluebird-02.fw'
Resolving [www.itee.uq.edu.au](www.itee.uq.edu.au)... 130.102.79.1
Connecting to [www.itee.uq.edu.au|130.102.79.1|:80](www.itee.uq.edu.au|130.102.79.1|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
15:18:35 ERROR 404: Not Found.

slick@slick-desktop:/lib/firmware$    < obviously i have missed something ...the search continues

---

### Post by slick1a on 2008-09-28
Kaffeine-Xine...
Ok.
KDE...
Found version: 3.5.9
Ok.WIN32 Codecs...
Ok.
libdvdcss...
Ok.
DVD Drive...
Ok.
DVB-Device...
Ok.
Distribution...
Ok.
RESULT: All ok!

SNR 100% no channels , nothing ...grr  grrr and double grrrrr !!!!!

---

### Post by avacado on 2009-10-10
Can anybody using a DVICO hybrid DVB-T card let me know how tey made it work.
I have been fiddling for ages and lost my drivers again.
obviously you might need to repeat the process if you had a HDD crash or distibution upgrade, somebody must have written it down...

---

### Post by avacado on 2009-10-10
I suggest we all register with DVICO as a means to let them know that we own the card and use DVICO products.

[http://www.fusionhdtv.co.kr/ENG/Support/](http://www.fusionhdtv.co.kr/ENG/Support/)

---

### Post by Stolea on 2009-10-17
> **avacado said:**
> I suggest we all register with DVICO as a means to let them know that we own the card and use DVICO products.

[http://www.fusionhdtv.co.kr/ENG/Support/](http://www.fusionhdtv.co.kr/ENG/Support/)

Good luck with that! I can't even get them to answer any queries on Windoze drivers! Sorry to be negative, but nice as their products are when they work, their backup is pretty lousy.
I think my next card will be a Hauppage 2200.

---

