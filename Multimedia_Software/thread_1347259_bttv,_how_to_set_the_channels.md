---
title: "bttv, how to set the channels?"
date: 2009-12-06
forum: Multimedia Software
---

### Post by frenchn00b on 2009-12-06
Hello

I have a blue screen as it can be seen here.
Any ideas to see teh channels?

I have 
```
# cat /proc/asound/cards
 0 [default        ]: USB-Audio - AK5370          
                      AKM              AK5370           at usb-0000:00:02.1-2, full speed
 1 [default_1      ]: USB-Audio - PnP Audio Device        
                      PnP Audio Device         at usb-0000:00:02.1-4, full speed

```

 
```
# cat /proc/asound/cards
 0 [default     ]: USB-Audio - PnP Audio Device        
                      PnP Audio Device         at usb-0000:00:02.1-4, full speed
 1 [default_1         ]: USB-Audio - AK5370          
                      AKM              AK5370           at usb-0000:00:02.1-2, full speed


```

my dmesg indicates:
```
 4.289035] usb 3-2: New USB device found, idVendor=0556, idProduct=0001
[    4.289038] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    4.289041] usb 3-2: Product: AK5370          
[    4.289042] usb 3-2: Manufacturer: AKM             
[    4.289109] usb 3-2: configuration #1 chosen from 1 choice
[    4.596032] usb 3-4: new full speed USB device using ohci_hcd and address 3
[    4.596072] hdc: host max PIO5 wanted PIO255(auto-tune) selected PIO4
[    4.596171] hdc: UDMA/66 mode selected
[    4.596304] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    4.611027] ide1 at 0x170-0x177,0x376 on irq 15
[    4.611331] sata_nv 0000:00:0a.0: version 3.5
[    4.611601] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 21
[    4.611605] sata_nv 0000:00:0a.0: PCI INT A -> Link[LTID] -> GSI 21 (level, low) -> IRQ 21
[    4.611634] sata_nv 0000:00:0a.0: setting latency timer to 64
[    4.611677] scsi0 : sata_nv
[    4.611751] scsi1 : sata_nv
[    4.612194] ata1: SATA max UDMA/133 cmd 0xf80 ctl 0xf00 bmdma 0xe000 irq 21
[    4.612197] ata2: SATA max UDMA/133 cmd 0xe80 ctl 0xe00 bmdma 0xe008 irq 21
[    4.806034] usb 3-4: New USB device found, idVendor=0d8c, idProduct=0201
[    4.806038] usb 3-4: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[    4.806040] usb 3-4: Product: PnP Audio Device        
[    4.806107] usb 3-4: configuration #1 chosen from 1 choice
[    5.254944] ide-gd driver 1.18
[    5.254972] hda: max request size: 512KiB
[    5.258359] ide-cd driver 5.00
[    5.258369] hda: 234441648 sectors (120034 MB) w/8192KiB Cache, CHS=16383/255/63
[    5.258762] hda: cache flushes supported
[    5.258801]  hda: hda1 hda2 < hda5 hda6 hda7 > hda3
[    5.334957] ide-cd: hdc: ATAPI 48X DVD-ROM DVD-R/RAM CD-R/RW drive, 2048kB Cache
[    5.334964] Uniform CD-ROM driver Revision: 3.20
[    5.981592] PM: Starting manual resume from disk
[    6.038889] kjournald starting.  Commit interval 5 seconds
[    6.038902] EXT3-fs: mounted filesystem with ordered data mode.
[    7.500906] udevd version 125 started
[    7.815041] Linux agpgart interface v0.103
[    7.817365] agpgart-amd64 0000:00:00.0: AGP bridge [10de/00e1]
[    7.817390] agpgart-amd64 0000:00:00.0: aperture size 4096 MB is not right, using settings from NB
[    7.817394] agpgart-amd64 0000:00:00.0: setting up Nforce3 AGP
[    7.833006] agpgart-amd64 0000:00:00.0: AGP aperture is 512M @ 0xc0000000
[    7.945067] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x5000
[    7.945081] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x5040
[    8.052716] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    8.052723] ACPI: Power Button [PWRF]
[    8.052793] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[    8.052796] ACPI: Power Button [PWRB]
[    8.097668] processor ACPI_CPU:00: registered as cooling_device0
[    8.097699] processor ACPI_CPU:01: registered as cooling_device1
[    8.382280] input: USB Optical Mouse USB Optical Mouse as /devices/pci0000:00/0000:00:02.0/usb1/1-1/1-1:1.0/input/input4
[    8.382328] a4tech 0003:09DA:0006.0001: input,hidraw2: USB HID v1.10 Mouse [USB Optical Mouse USB Optical Mouse] on usb-0000:00:02.0-1/input0
[    8.575155] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    8.588074] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    8.736034] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[    8.793015] input: PC Speaker as /devices/platform/pcspkr/input/input5
[    9.474067] Linux video capture interface: v2.00
[    9.565013] bttv: driver version 0.9.18 loaded
[    9.565017] bttv: using 8 buffers with 2080k (520 pages) each for capture
[    9.565052] bttv: Bt8xx card found (0).
[    9.565299] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 19
[    9.565309] bttv 0000:02:09.0: PCI INT A -> Link[LNKB] -> GSI 19 (level, low) -> IRQ 19
[    9.565318] bttv0: Bt878 (rev 2) at 0000:02:09.0, irq: 19, latency: 32, mmio: 0xfbffe000
[    9.565342] bttv0: detected: FlyVideo 98 (LR50)/ Chronos Video Shuttle II [card=35], PCI subsystem ID is 1851:1850
[    9.565345] bttv0: using: Lifeview FlyVideo 98 LR50 / Chronos Video Shuttle II [card=35,autodetected]
[    9.565348] IRQ 19/bttv0: IRQF_DISABLED is not guaranteed on shared IRQs
[    9.565381] bttv0: gpio: en=00000000, out=00000000 in=008dff00 [init]
[    9.565427] bttv0: FlyVideo_gpio: unknown tuner type.
[    9.565430] bttv0: FlyVideo Radio=no  RemoteControl=yes Tuner=-1 gpio=0x8dff00
[    9.565432] bttv0: FlyVideo  LR90=no  tda9821/tda9820=no  capture_only=no 
[    9.565435] bttv0: tuner type unset
[    9.565468] bttv0: registered device video0
[    9.565487] bttv0: registered device vbi0

```

---

### Post by xc3RnbFO8P on 2009-12-06
Try:
> modprobe card=35 tuner=2
and do dmesg again or try to scan with Tvtime.

From Tvtime site:
```
6. Unable to tune to channels using the bttv, saa7134 or cx88 drivers

The bttv, saa7134, and cx88 drivers each support a wide variety of cards 
which all use the same chip. In particular, these cards differ in what tuner they use, 
how many inputs they have, and how it is configured.

Often, these drivers cannot autodetect the card type, or detect the incorrect card. 
To debug this, you must watch your kernels logs by running the "dmesg" command, 
potentially loading and unloading the driver with different options until the driver 
is successfully loaded.

Some hints:
If your card appears as UNKNOWN/GENERIC, then the tuner driver will not be loaded 
and the card will likely not work. You will need to load the driver with the 
correct card number. 
If your tuner reports that it is using type -1, it is not loaded and you will 
not be able to tune any stations. 
If you are an NTSC user, make sure the tuner you are using 
announces itself as an NTSC tuner. 

For example, if you are using the bttv driver, the common 
procedure for setting up a card is as follows:
Run "modprobe bttv" with no options. 
Run "dmesg". Check to see if your card is autodetected, 
and if the tuner is correct. If everything looks fine, you're done. 
If the card appears as UNKNOWN/GENERIC, find the CARDLIST file in 
your kernel documentation and find your card in the list. 
Unload bttv and tuner using "rmmod bttv" and "rmmod tuner". 
Run "modprobe bttv card=X" where X is the number of your card. 
Run "dmesg" again. See if the card loaded properly and if the tuner is correct. 
If not, unload bttv and tuner again, and try specifying the tuner type as well using "modprobe bttv card=X tuner=Y". 
Curse Linux for being so complicated.
```

---

### Post by frenchn00b on 2009-12-06
> **Ringi said:**
> Try:

and do dmesg again or try to scan with Tvtime.

From Tvtime site:
```
6. Unable to tune to channels using the bttv, saa7134 or cx88 drivers

The bttv, saa7134, and cx88 drivers each support a wide variety of cards 
which all use the same chip. In particular, these cards differ in what tuner they use, 
how many inputs they have, and how it is configured.

Often, these drivers cannot autodetect the card type, or detect the incorrect card. 
To debug this, you must watch your kernels logs by running the "dmesg" command, 
potentially loading and unloading the driver with different options until the driver 
is successfully loaded.

Some hints:
If your card appears as UNKNOWN/GENERIC, then the tuner driver will not be loaded 
and the card will likely not work. You will need to load the driver with the 
correct card number. 
If your tuner reports that it is using type -1, it is not loaded and you will 
not be able to tune any stations. 
If you are an NTSC user, make sure the tuner you are using 
announces itself as an NTSC tuner. 

For example, if you are using the bttv driver, the common 
procedure for setting up a card is as follows:
Run "modprobe bttv" with no options. 
Run "dmesg". Check to see if your card is autodetected, 
and if the tuner is correct. If everything looks fine, you're done. 
If the card appears as UNKNOWN/GENERIC, find the CARDLIST file in 
your kernel documentation and find your card in the list. 
Unload bttv and tuner using "rmmod bttv" and "rmmod tuner". 
Run "modprobe bttv card=X" where X is the number of your card. 
Run "dmesg" again. See if the card loaded properly and if the tuner is correct. 
If not, unload bttv and tuner again, and try specifying the tuner type as well using "modprobe bttv card=X tuner=Y". 
[COLOR="Red"]**Curse Linux for being so complicated.**[/COLOR]
```


```

tvtime-scanner -d /dev/video0 -n NTSC
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/winwood/.tvtime/tvtime.xml
Scanning using TV standard NTSC.
/home/winwood/.tvtime/stationlist.xml: No existing NTSC station list "Custom".
videoinput: Can't get tuner info: Invalid argument
videoinput: Can't get tuner info: Invalid argument

    No tuner found on input 2.  If you have a tuner, please
    select a different input using --input=<num>.
```



if I run a script, will it kill teh pc bttv card?


```
for X in  ` seq 1 1 200` ; do 
for Y in  ` seq 1 1 200` ; do 
rmmod bttv
modprobe bttv card=$X tuner=$Y
tvtime-scanner -d /dev/video0 -n NTSC
tvtime 
done
done 
 
```

---

