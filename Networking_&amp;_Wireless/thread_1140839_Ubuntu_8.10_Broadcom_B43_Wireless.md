---
title: "Ubuntu 8.10 Broadcom B43 Wireless"
date: 2009-04-28
forum: Networking &amp; Wireless
---

### Post by Viligam on 2009-04-28
Hi Everyone,

I did my best to scour the forums to see if I could find an answer prior to posting but could not find anything that seemed to do the trick.  So, I am using a Broadcom B43 and cannot seem to connect / see any wireless networks.

If anyone has any suggestions I am all ears.  Also I did not install the NDIS wrapper because I just wanted to make I needed to before going forward.  I thought I got it running at some point in the past without the wrapper, but I am open to any and all suggestions at this point. 

```
...:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
``````
...:~$ ndiswrapper -l
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
``````
...:~$ lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc Radeon Xpress 200 (RS480/RS482/RX480/RX482) Chipset - Host bridge [1002:5951] (rev 01)
00:02.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI-X Root Port [1002:5a34]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a38]
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374]
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375]
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373]
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 11)
00:14.1 IDE interface [0101]: ATI Technologies Inc IXP SB400 IDE Controller [1002:4376]
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377]
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371]
00:14.5 Multimedia audio controller [0401]: ATI Technologies Inc IXP SB400 AC'97 Audio Controller [1002:4370] (rev 02)
00:14.6 Modem [0703]: ATI Technologies Inc SB400 AC'97 Modem Controller [1002:4378] (rev 02)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc M24 1P [Radeon Mobility X600] [1002:3150]
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller [11ab:4351] (rev 10)
03:05.0 CardBus bridge [0607]: ENE Technology Inc CB1410 Cardbus Controller [1524:1410] (rev 01)
03:07.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
03:0e.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller [1106:3044] (rev 80)
```:popcorn:

---

### Post by thewolfman on 2009-04-28
Did you install the Broadcom firmware and if you do use ndiswrapper you will need the Windows driver cd with your wlan driver file ending in INF which you can install with the Windows wireless drivers app (ndiswrapper) assuming you installed the GUI for ndiswrapper!.

I have a Broadcom too and it works for me.
If this doesn't help you, try typing in the search bar: broadcom and this will give you a list of posts about the topic in more depth.


thewolfman

---

### Post by Viligam on 2009-04-28
I do not think that Driver exists anywhere on the net that I could find.  Possibly due to age or now outdated technology.  

Does anyone have copies of the drivers they can e-mail me?  [EMAIL="Viligam@gmail.com"]Viligam@gmail.com[/EMAIL]

Would Upgrading to 9.04 resolve the issue?

Does anyone have any other ideas?

---

### Post by Ayuthia on 2009-04-28
If you have a working internet connection, you should be able to install the firmware by going into System->Administration->Hardware Drivers and activating the Broadcom option.

Also, are you using an Acer?  Sometimes an additional step is needed for some Acer models.

---

### Post by Viligam on 2009-04-28
Nope, I am using a Gateway laptop.

I am able to install the drivers I just cannot view or connect to any networks.  To the best of my knowledge they are install but why can I not view or connect wireless networks?

When I run an iwconfig I get:

```
:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

---

### Post by Ayuthia on 2009-04-28
Can you post the results of:
```
dmesg|grep b43
```
Sometimes dmesg can provide some clues about what is happening when it loads the b43 module.

---

### Post by abn91c on 2009-04-28
make sure double check you router settings/password/security keys as that card should work with 8.10 and 9.04, check this post I linked my broadcom drivers that I used on 8.04(post #3)
[http://ubuntuforums.org/showthread.php?t=1141998&highlight=abn91c](http://ubuntuforums.org/showthread.php?t=1141998&highlight=abn91c)

---

### Post by Viligam on 2009-04-28
results of 

```
:~$ dmesg|grep b43
[    3.493291] b43-pci-bridge 0000:03:07.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   14.701031] b43-phy0: Broadcom 4318 WLAN found
[   29.696202] input: b43-phy0 as /devices/virtual/input/input9
[   29.801232] firmware: requesting b43/ucode5.fw
[   29.878277] firmware: requesting b43/pcm5.fw
[   29.880939] firmware: requesting b43/b0g0initvals5.fw
[   29.890908] firmware: requesting b43/b0g0bsinitvals5.fw
[   30.100034] b43-phy0: Loading firmware version 351.126 (2006-07-29 05:54:02)
[   30.100042] b43-phy0 warning: You are using an old firmware image. Support for old firmware will be removed in July 2008.
[   30.100045] b43-phy0 warning: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[   30.224447] Registered led device: b43-phy0::tx
[   30.224647] Registered led device: b43-phy0::rx
[   30.224775] Registered led device: b43-phy0::radio
[   30.724021] b43-phy0: Radio hardware status changed to DISABLED
```

---

### Post by sir_nasty on 2009-04-28
30.100034] b43-phy0: Loading firmware version 351.126 (2006-07-29 05:54:02)
[   30.100042] b43-phy0 warning: You are using an old firmware image. Support for old firmware will be removed in July 2008.
[   30.100045] b43-phy0 warning: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the latest firmware (version 4)


Have you checked the site for a new firmware?

---

### Post by sir_nasty on 2009-04-28
run uname -r and go to the link/site above and make sure you have the current firware.

---

### Post by Viligam on 2009-04-28
I just checked it out and it says that I have the most up to date firmware.

```
:~$ sudo apt-get install b43-fwcutter
[sudo] password for ...: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by Viligam on 2009-04-28
> **sir_nasty said:**
> run uname -r and go to the link/site above and make sure you have the current firware.


What is the full command line?

I tried running ... 
```
run uname -r sudo apt-get install b43-fwcutter
```

and

```
sudo apt-get install b43-fwcutter run uname -r
```

Neither of which seem to do the trick.

---

### Post by Ayuthia on 2009-04-29
The command should be:
```
uname -r
```


Can you also check and see if you have installed b43-fwcutter:
```
dpkg -l b43-fwcutter
```

You might want to move the current b43 folder just in case:
```
sudo mv /lib/firmware/b43 /lib/firmware/b43-old
```

If dpkg -l comes back with a version number of b43-fwcutter then it has already been installed.  You can have it download the firmware again by doing:
```
sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh
```After it has finished:
```
sudo modprobe -r b43 ssb
sudo modprobe b43
sudo ifconfig wlan0 up
sudo iwlist scan
```
You should be able to see wireless sites.  If not, then please post:
```
dmesg|grep b43
```again.

If b43-fwcutter has not been installed, then still move the b43 folder and install b43-fwcutter:
```
sudo apt-get install b43-fwcutter
```

---

### Post by Viligam on 2009-04-29
Thanks!  I followed the directions step by step and here are the respective results.

I did also move and reinstall the firmware as described in the steps.

```
:~$ uname -r
2.6.27-11-generic

``````
:~$ dpkg -l b43-fwcutter
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  b43-fwcutter   1:011-4ubuntu1 Utility for extracting Broadcom 43xx firmwar
``````

:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results
```
```
:~$ dmesg|grep b43
[    3.493291] b43-pci-bridge 0000:03:07.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   14.701031] b43-phy0: Broadcom 4318 WLAN found
[   29.696202] input: b43-phy0 as /devices/virtual/input/input9
[   29.801232] firmware: requesting b43/ucode5.fw
[   29.878277] firmware: requesting b43/pcm5.fw
[   29.880939] firmware: requesting b43/b0g0initvals5.fw
[   29.890908] firmware: requesting b43/b0g0bsinitvals5.fw
[   30.100034] b43-phy0: Loading firmware version 351.126 (2006-07-29 05:54:02)
[   30.100042] b43-phy0 warning: You are using an old firmware image. Support for old firmware will be removed in July 2008.
[   30.100045] b43-phy0 warning: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[   30.224447] Registered led device: b43-phy0::tx
[   30.224647] Registered led device: b43-phy0::rx
[   30.224775] Registered led device: b43-phy0::radio
[   30.724021] b43-phy0: Radio hardware status changed to DISABLED
[29929.252158] b43-pci-bridge 0000:03:07.0: PCI INT A disabled
[29939.379563] b43-pci-bridge 0000:03:07.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[29939.503138] b43-phy0: Broadcom 4318 WLAN found
[29943.717220] input: b43-phy0 as /devices/virtual/input/input11
[29943.800463] firmware: requesting b43/ucode5.fw
[29943.805267] firmware: requesting b43/pcm5.fw
[29943.815186] firmware: requesting b43/b0g0initvals5.fw
[29943.844450] firmware: requesting b43/b0g0bsinitvals5.fw
[29943.976083] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[29944.103372] Registered led device: b43-phy0::tx
[29944.103802] Registered led device: b43-phy0::rx
[29944.104202] Registered led device: b43-phy0::radio
[29944.732311] b43-phy0: Radio hardware status changed to DISABLED
[29944.813089] b43-phy0: Radio turned on by software
[29944.813103] b43-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
```

---

### Post by kevdog on 2009-04-29
The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.

You need to turn the wireless card on -- Meaning either use an external button or activate it in the BIOS.  There may also be a key combination (ie alt-F5 or something like that) to activate the wireless.

---

### Post by Viligam on 2009-04-29
Kevdog, that did it!  Thanks!

It is up and running as it should be now!

A HUGE thanks to Ayuthia for showing me what to do to get it working!!! :KS

---

### Post by yogo on 2009-05-01
> **kevdog said:**
> The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.

You need to turn the wireless card on -- Meaning either use an external button or activate it in the BIOS.  There may also be a key combination (ie alt-F5 or something like that) to activate the wireless.

I am not exactly sure what you mean by turning on and off built in wireless?

I did try bios and lt-F5 and a few others.
I picked up a Gateway MX118 that had XP media edition and I found it to be sluggish reminiscent of XP home. 

So I put 9.04 on it immeadiately. Had a few issues with wireless but very close to out of the box. 9.04 does work out of the box on both a Dell Desktop and laptop.

What I had to do to get mine going was hardwire the Gateway laptop, download Wicd, then remove network manager. Install Wicd, hardwire temporarily, update the restricted driver ie fwcutter , then play around with Wicd and got wireless going very easy. I am not sure if it would work with network manager but it works with Wicd so I am going to leave it alone.

Anyways this thread and another here helped me last night while I was trouble shooting this.

Here is my dmesg
```

  1.734385] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[    1.734858] ACPI: Lid Switch [LID]
[    1.734995] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    1.735013] processor ACPI_CPU:00: registered as cooling_device0
[    1.735016] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.739064] isapnp: Scanning for PnP cards...
[    2.093370] isapnp: No Plug & Play device found
[    2.094299] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.094559] serial 0000:00:14.6: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.094567] serial 0000:00:14.6: PCI INT B disabled
[    2.095120] brd: module loaded
[    2.095384] loop: module loaded
[    2.095442] Fixed MDIO Bus: probed
[    2.095447] PPP generic driver version 2.4.2
[    2.095500] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    2.095520] Driver 'sd' needs updating - please use bus_type methods
[    2.095527] Driver 'sr' needs updating - please use bus_type methods
[    2.095751] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.095795] pata_atiixp 0000:00:14.1: setting latency timer to 64
[    2.095891] scsi0 : pata_atiixp
[    2.095985] scsi1 : pata_atiixp
[    2.097034] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8410 irq 14
[    2.097036] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8418 irq 15
[    2.260764] ata1.00: ATA-7: FUJITSU MHV2080AT PL, 000000A0, max UDMA/100
[    2.260767] ata1.00: 156301488 sectors, multi 16: LBA 
[    2.276716] ata1.00: configured for UDMA/100
[    2.464650] ata2.00: ATAPI: TSSTcorpCD/DVDW TS-L532U, GA03, max UDMA/33
[    2.496668] ata2.00: configured for UDMA/33
[    2.497401] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHV2080A 0000 PQ: 0 ANSI: 5
[    2.497474] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[    2.497488] sd 0:0:0:0: [sda] Write Protect is off
[    2.497490] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.497509] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.497559] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[    2.497569] sd 0:0:0:0: [sda] Write Protect is off
[    2.497571] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.497589] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.497593]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    2.723966] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.724010] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.759596] scsi 1:0:0:0: CD-ROM            TSSTcorp CD/DVDW TS-L532U GA03 PQ: 0 ANSI: 5
[    2.768997] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    2.769000] Uniform CD-ROM driver Revision: 3.20
[    2.769071] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.769104] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.769466] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.769485] ehci_hcd 0000:00:13.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.769510] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    2.769568] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[    2.769632] ehci_hcd 0000:00:13.2: irq 19, io mem 0xd0002000
[    2.780007] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    2.780071] usb usb1: configuration #1 chosen from 1 choice
[    2.780095] hub 1-0:1.0: USB hub found
[    2.780104] hub 1-0:1.0: 8 ports detected
[    2.780216] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.780230] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.780241] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    2.780274] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    2.780290] ohci_hcd 0000:00:13.0: irq 19, io mem 0xd0000000
[    2.840040] usb usb2: configuration #1 chosen from 1 choice
[    2.840060] hub 2-0:1.0: USB hub found
[    2.840071] hub 2-0:1.0: 4 ports detected
[    2.840149] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.840159] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    2.840193] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    2.840208] ohci_hcd 0000:00:13.1: irq 19, io mem 0xd0001000
[    2.900046] usb usb3: configuration #1 chosen from 1 choice
[    2.900067] hub 3-0:1.0: USB hub found
[    2.900077] hub 3-0:1.0: 4 ports detected
[    2.900157] uhci_hcd: USB Universal Host Controller Interface driver
[    2.900210] usbcore: registered new interface driver libusual
[    2.900237] usbcore: registered new interface driver usbserial
[    2.900246] USB Serial support registered for generic
[    2.900257] usbcore: registered new interface driver usbserial_generic
[    2.900259] usbserial: USB Serial Driver core
[    2.900295] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    2.903646] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.903650] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.903745] mice: PS/2 mouse device common for all mice
[    2.903896] rtc_cmos 00:04: RTC can wake from S4
[    2.903936] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    2.903964] rtc0: alarms up to one month, 114 bytes nvram
[    2.904023] device-mapper: uevent: version 1.0.3
[    2.904116] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    2.904163] device-mapper: multipath: version 1.0.5 loaded
[    2.904166] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.904235] EISA: Probing bus 0 at eisa.0
[    2.904244] Cannot allocate resource for EISA slot 1
[    2.904273] Cannot allocate resource for EISA slot 8
[    2.904275] EISA: Detected 0 cards.
[    2.904323] cpuidle: using governor ladder
[    2.904360] cpuidle: using governor menu
[    2.904776] TCP cubic registered
[    2.904858] NET: Registered protocol family 10
[    2.905192] lo: Disabled Privacy Extensions
[    2.905450] NET: Registered protocol family 17
[    2.905465] Bluetooth: L2CAP ver 2.11
[    2.905466] Bluetooth: L2CAP socket layer initialized
[    2.905468] Bluetooth: SCO (Voice Link) ver 0.6
[    2.905470] Bluetooth: SCO socket layer initialized
[    2.905491] Bluetooth: RFCOMM socket layer initialized
[    2.905497] Bluetooth: RFCOMM TTY layer initialized
[    2.905498] Bluetooth: RFCOMM ver 1.10
[    2.905518] powernow-k8: Found 1 Mobile AMD Athlon(tm) 64 Processor 3400+ processors (1 cpu cores) (version 2.20.00)
[    2.905554] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x8
[    2.905556] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xa
[    2.905558] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xc
[    2.905560] powernow-k8:    3 : fid 0x8 (1600 MHz), vid 0xe
[    2.905561] powernow-k8:    4 : fid 0x0 (800 MHz), vid 0x18
[    2.905596] Using IPI No-Shortcut mode
[    2.905653] registered taskstats version 1
[    2.905747]   Magic number: 9:297:124
[    2.905849] rtc_cmos 00:04: setting system clock to 2009-05-01 11:08:35 UTC (1241176115)
[    2.905852] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.905854] EDD information not available.
[    2.906362] Freeing unused kernel memory: 532k freed
[    2.906472] Write protecting the kernel text: 4128k
[    2.906510] Write protecting the kernel read-only data: 1532k
[    2.947084] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    3.262326] sky2 driver version 1.22
[    3.262375] sky2 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.262387] sky2 0000:02:00.0: setting latency timer to 64
[    3.262448] sky2 0000:02:00.0: Yukon-2 FE chip revision 1
[    3.326096] sky2 0000:02:00.0: Marvell Yukon 88E8036 Fast Ethernet Controller
[    3.326098]  Part Number: Yukon 88E8036
[    3.326100]  Engineering Level: Rev. 1.3
[    3.326101]  Manufacturer: Marvell
[    3.329668] sky2 eth0: addr 00:03:25:28:99:88
[    3.360784] b43-pci-bridge 0000:08:07.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    3.364294] ssb: Sonics Silicon Backplane found on PCI device 0000:08:07.0
[    3.381385] ohci1394 0000:08:0e.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.434157] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[23]  MMIO=[d0303000-d03037ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.672622] Marking TSC unstable due to TSC halts in idle
[    3.877717] PM: Starting manual resume from disk
[    3.877720] PM: Resume from partition 8:6
[    3.877721] PM: Checking hibernation image.
[    3.877997] PM: Resume from disk failed.
[    3.922664] kjournald starting.  Commit interval 5 seconds
[    3.922673] EXT3-fs: mounted filesystem with ordered data mode.
[    4.748145] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000325215000e034]
[   11.163406] udev: starting version 141
[   11.329445] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.572304] Linux agpgart interface v0.103
[   11.603153] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8400, revision 0
[   11.631654] yenta_cardbus 0000:08:05.0: CardBus bridge found [107b:0506]
[   11.631685] yenta_cardbus 0000:08:05.0: Using CSCINT to route CSC interrupts to PCI
[   11.631688] yenta_cardbus 0000:08:05.0: Routing CardBus interrupts to PCI
[   11.631694] yenta_cardbus 0000:08:05.0: TI: mfunc 0x01001002, devctl 0x44
[   11.653380] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   11.820292] cfg80211: Calling CRDA to update world regulatory domain
[   11.836082] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   11.861119] yenta_cardbus 0000:08:05.0: ISA IRQ mask 0x0cf8, PCI irq 22
[   11.861124] yenta_cardbus 0000:08:05.0: Socket status: 30000006
[   11.861130] yenta_cardbus 0000:08:05.0: pcmcia: parent PCI bridge I/O window: 0xb000 - 0xbfff
[   11.861134] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xb000-0xbfff: clean.
[   11.861298] yenta_cardbus 0000:08:05.0: pcmcia: parent PCI bridge Memory window: 0xd0300000 - 0xd03fffff
[   11.861301] yenta_cardbus 0000:08:05.0: pcmcia: parent PCI bridge Memory window: 0x68000000 - 0x6bffffff
[   11.917870] cfg80211: World regulatory domain updated:
[   11.917874]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   11.917877]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.917879]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.917881]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.917883]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.917885]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.628239] b43-phy0: Broadcom 4306 WLAN found
[   12.676859] phy0: Selected rate control algorithm 'pid'
[   12.731538] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x23aeb3, caps: 0xa04713/0x10008
[   12.769838] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   12.793453] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   12.795793] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   12.796854] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   12.797662] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   12.798497] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   12.849811] ATI IXP AC97 controller 0000:00:14.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   12.862115] ATI IXP MC97 controller 0000:00:14.6: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   12.874280] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]
[   12.972068] MC'97 0 converters and GPIO not ready (0x1)
[   13.108785] lp: driver loaded but no devices found
[   13.163345] Adding 1116476k swap on /dev/sda6.  Priority:-1 extents:1 across:1116476k
[   13.181170] EXT3 FS on sda5, internal journal
[   13.680460] type=1505 audit(1241190526.274:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1888
[   13.726967] type=1505 audit(1241190526.318:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1892
[   13.727133] type=1505 audit(1241190526.318:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1892
[   13.727184] type=1505 audit(1241190526.318:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1892
[   13.727229] type=1505 audit(1241190526.318:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1892
[   13.864790] type=1505 audit(1241190526.458:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1897
[   13.865046] type=1505 audit(1241190526.458:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1897
[   13.892553] type=1505 audit(1241190526.486:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1901
[   17.749917] input: b43-phy0 as /devices/virtual/input/input8
[   17.780079] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   17.822871] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   17.822876] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[   17.889828] sky2 eth0: enabling interface
[   17.890036] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.193079] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.193082] Bluetooth: BNEP filters: protocol multicast
[   18.215963] Bridge firewalling registered
[   19.329598] ppdev: user-space parallel port driver
[   19.345707] pci 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   19.697537] [drm] Initialized drm 1.1.0 20060810
[   19.786109] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   20.362213] [drm] Setting GART location based on new memory map
[   20.362805] [drm] Loading R300 Microcode
[   20.362826] [drm] Num pipes: 4
[   20.362832] [drm] writeback test succeeded in 1 usecs
[   24.706020] input: b43-phy0 as /devices/virtual/input/input9
[   24.719592] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   24.721892] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   24.721898] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[   28.631852] input: b43-phy0 as /devices/virtual/input/input10
[   28.639590] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[ [COLOR=Red]  28.641892] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   28.641896] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[   32.632999] input: b43-phy0 as /devices/virtual/input/input11
[   32.640726] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   32.642771] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   32.642775] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).[/COLOR]
[   67.098051] input: b43-phy0 as /devices/virtual/input/input12
[   67.105938] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   67.107979] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   67.107983] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[   68.233882] input: b43-phy0 as /devices/virtual/input/input13
[   68.242645] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   68.244955] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   68.244960] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[   69.371076] input: b43-phy0 as /devices/virtual/input/input14
[   69.379071] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   69.381369] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   69.381375] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[   70.746544] input: b43-phy0 as /devices/virtual/input/input15
[   70.754481] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   70.756782] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   70.756787] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[   81.972053] Clocksource tsc unstable (delta = -302761342 ns)
[  196.452008] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[  196.452516] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  206.852044] eth0: no IPv6 routers present
[  219.260056] sky2 eth0: disabling interface
[  219.516080] input: b43-phy0 as /devices/virtual/input/input16
[  219.532976] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[  219.538505] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[  219.538515] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[  219.573169] sky2 eth0: enabling interface
[  219.573740] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  221.256291] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[  221.256810] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  231.628025] eth0: no IPv6 routers present
[  270.784819] b43-phy1: Broadcom 4306 WLAN found
[  270.835546] phy1: Selected rate control algorithm 'pid'
[  386.656114] type=1505 audit(1241190899.250:10): operation="profile_replace" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=5683
[  386.712043] type=1505 audit(1241190899.306:11): operation="profile_replace" name="/sbin/dhclient-script" name2="default" pid=5687
[  386.712349] type=1505 audit(1241190899.306:12): operation="profile_replace" name="/sbin/dhclient3" name2="default" pid=5687
[  386.712406] type=1505 audit(1241190899.306:13): operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=5687
[  386.712458] type=1505 audit(1241190899.306:14): operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=5687
[  386.864642] type=1505 audit(1241190899.458:15): operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=5692
[  386.865058] type=1505 audit(1241190899.458:16): operation="profile_replace" name="/usr/sbin/cupsd" name2="default" pid=5692
[  386.904294] type=1505 audit(1241190899.498:17): operation="profile_replace" name="/usr/sbin/tcpdump" name2="default" pid=5696
[  551.171929] sky2 eth0: Link is down.
[  552.663032] input: b43-phy1 as /devices/virtual/input/input17
[  552.728264] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[  552.740606] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[  552.749518] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[  552.758466] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[  552.880081] b43-phy1: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  552.942843] Registered led device: b43-phy1::tx
[  552.942884] Registered led device: b43-phy1::rx
[  552.942926] Registered led device: b43-phy1::radio
[  552.960087] b43-phy1: Radio turned on by software
[  552.960776] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  565.335420] input: b43-phy1 as /devices/virtual/input/input18
[  565.492075] b43-phy1: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  565.555021] Registered led device: b43-phy1::tx
[  565.555063] Registered led device: b43-phy1::rx
[  565.555114] Registered led device: b43-phy1::radio
[  565.589806] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  565.748620] wlan0: authenticate with AP 00:16:01:27:7a:7b
[  565.769917] wlan0: authenticate with AP 00:16:01:27:7a:7b
[  565.771472] wlan0: authenticated
[  565.771481] wlan0: associate with AP 00:16:01:27:7a:7b
[  565.773691] wlan0: RX AssocResp from 00:16:01:27:7a:7b (capab=0x421 status=0 aid=2)
[  565.773698] wlan0: associated
[  565.774328] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  576.620044] wlan0: no IPv6 routers present
[ 2083.472058] usb 1-4: new high speed USB device using ehci_hcd and address 2
[ 2083.643089] usb 1-4: configuration #1 chosen from 1 choice
[ 2083.874651] Linux video capture interface: v2.00
[ 2084.300830] usbcore: registered new interface driver snd-usb-audio
[ 2084.316367] uvcvideo: Found UVC 1.00 device Microsoft LifeCam NX-3000 (045e:0721)
[ 2084.317166] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[ 2084.318254] input: Microsoft LifeCam NX-3000 as /devices/pci0000:00/0000:00:13.2/usb1/1-4/1-4:1.0/input/input19
[ 2084.328308] usbcore: registered new interface driver uvcvideo
[ 2084.328317] USB Video Class driver (v0.1.0)
[ 2086.141176] 2:3:1: cannot set freq 48000 to ep 0x84
[ 2142.225820] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[ 7734.853786] input: b43-phy1 as /devices/virtual/input/input20
[ 7735.040089] b43-phy1: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 7735.102913] Registered led device: b43-phy1::tx
[ 7735.102956] Registered led device: b43-phy1::rx
[ 7735.103000] Registered led device: b43-phy1::radio
[ 7735.148951] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7743.052322] input: b43-phy1 as /devices/virtual/input/input21
[ 7743.212077] b43-phy1: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 7743.271203] Registered led device: b43-phy1::tx
[ 7743.271248] Registered led device: b43-phy1::rx
[ 7743.271291] Registered led device: b43-phy1::radio
[ 7743.316774] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7743.486501] wlan0: authenticate with AP 00:16:01:27:7a:7b
[ 7743.488552] wlan0: authenticated
[ 7743.488561] wlan0: associate with AP 00:16:01:27:7a:7b
[ 7743.519109] wlan0: RX AssocResp from 00:16:01:27:7a:7b (capab=0x421 status=0 aid=2)
[ 7743.519118] wlan0: associated
[ 7743.519780] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 7754.048035] wlan0: no IPv6 routers present
[10816.328613] usb 1-4: USB disconnect, address 2
[10816.624062] usb 1-4: new high speed USB device using ehci_hcd and address 3
[10816.796320] usb 1-4: configuration #1 chosen from 1 choice
[10816.796556] uvcvideo: Found UVC 1.00 device Microsoft LifeCam NX-3000 (045e:0721)
[10816.797311] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[10816.797982] input: Microsoft LifeCam NX-3000 as /devices/pci0000:00/0000:00:13.2/usb1/1-4/1-4:1.0/input/input22
[10818.988188] 3:3:1: cannot set freq 48000 to ep 0x84
[11015.123873] input: b43-phy1 as /devices/virtual/input/input23
[11015.315170] b43-phy1: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[11015.371003] Registered led device: b43-phy1::tx
[11015.371047] Registered led device: b43-phy1::rx
[11015.371089] Registered led device: b43-phy1::radio
[11015.412785] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[11016.668066] input: b43-phy1 as /devices/virtual/input/input24
[11016.832081] b43-phy1: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[11016.887023] Registered led device: b43-phy1::tx
[11016.887066] Registered led device: b43-phy1::rx
[11016.887108] Registered led device: b43-phy1::radio
[11016.972770] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[11017.149159] wlan0: direct probe to AP 00:16:01:27:7a:7b try 1
[11017.150804] wlan0 direct probe responded
[11017.150812] wlan0: authenticate with AP 00:16:01:27:7a:7b
[11017.173138] wlan0: authenticated
[11017.173149] wlan0: associate with AP 00:16:01:27:7a:7b
[11017.175071] wlan0: RX AssocResp from 00:16:01:27:7a:7b (capab=0x421 status=0 aid=2)
[11017.175078] wlan0: associated
[11017.175710] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[11027.512043] wlan0: no IPv6 routers present
[11201.280093] usb 1-4: USB disconnect, address 3
[11205.188062] usb 1-4: new high speed USB device using ehci_hcd and address 4
[11205.357972] usb 1-4: configuration #1 chosen from 1 choice
[11205.358308] uvcvideo: Found UVC 1.00 device Microsoft LifeCam NX-3000 (045e:0721)
[11205.358774] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[11205.359481] input: Microsoft LifeCam NX-3000 as /devices/pci0000:00/0000:00:13.2/usb1/1-4/1-4:1.0/input/input25
[11207.568305] 4:3:1: cannot set freq 48000 to ep 0x84
[11342.701502] usb 1-4: USB disconnect, address 4
[11346.516067] usb 1-3: new high speed USB device using ehci_hcd and address 5
[11346.685467] usb 1-3: configuration #1 chosen from 1 choice
[11346.686571] uvcvideo: Found UVC 1.00 device Microsoft LifeCam NX-3000 (045e:0721)
[11346.686980] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[11346.687838] input: Microsoft LifeCam NX-3000 as /devices/pci0000:00/0000:00:13.2/usb1/1-3/1-3:1.0/input/input26
[11348.884264] 5:3:1: cannot set freq 48000 to ep 0x84
[11568.359297] usb 1-3: USB disconnect, address 5
[11584.184060] usb 1-4: new high speed USB device using ehci_hcd and address 6
[11584.354097] usb 1-4: configuration #1 chosen from 1 choice
[11584.354459] uvcvideo: Found UVC 1.00 device Microsoft LifeCam NX-3000 (045e:0721)
[11584.354922] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[11584.355617] input: Microsoft LifeCam NX-3000 as /devices/pci0000:00/0000:00:13.2/usb1/1-4/1-4:1.0/input/input27
[11586.504199] 6:3:1: cannot set freq 48000 to ep 0x84
[12560.031432] usb 1-4: USB disconnect, address 6
[14489.480058] wlan0: No ProbeResp from current AP 00:16:01:27:7a:7b - assume out of range
[14504.672303] input: b43-phy1 as /devices/virtual/input/input28
[14504.836055] b43-phy1: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[14504.891742] Registered led device: b43-phy1::tx
[14504.891784] Registered led device: b43-phy1::rx
[14504.891824] Registered led device: b43-phy1::radio
[14504.936895] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[14505.089437] wlan0: direct probe to AP 00:16:01:27:7a:7b try 1
[14505.089477] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[14505.111360] wlan0 direct probe responded
[14505.111372] wlan0: authenticate with AP 00:16:01:27:7a:7b
[14505.112999] wlan0: authenticated
[14505.113007] wlan0: associate with AP 00:16:01:27:7a:7b
[14505.113013] wlan0: mismatch in privacy configuration and mixed-cell disabled - abort association
[14505.308057] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[14596.228095] input: b43-phy1 as /devices/virtual/input/input29
[14596.384075] b43-phy1: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[14596.460277] Registered led device: b43-phy1::tx
[14596.460321] Registered led device: b43-phy1::rx
[14596.460368] Registered led device: b43-phy1::radio
[14596.516829] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[14596.884132] wlan0: direct probe to AP 00:16:01:27:7a:7b try 1
[14596.884172] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[14596.885774] wlan0 direct probe responded
[14596.885782] wlan0: authenticate with AP 00:16:01:27:7a:7b
[14596.892398] wlan0: authenticated
[14596.892410] wlan0: associate with AP 00:16:01:27:7a:7b
[14596.892418] wlan0: mismatch in privacy configuration and mixed-cell disabled - abort association
[14596.958645] wlan0: authenticate with AP 00:16:01:27:7a:7b
[14596.960544] wlan0: authenticated
[14596.960552] wlan0: associate with AP 00:16:01:27:7a:7b
[14596.962374] wlan0: RX AssocResp from 00:16:01:27:7a:7b (capab=0x431 status=0 aid=1)
[14596.962380] wlan0: associated
[14596.963206] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[14607.648046] wlan0: no IPv6 routers present
[14715.352069] usb 1-4: new high speed USB device using ehci_hcd and address 7
[14715.932318] usb 1-4: configuration #1 chosen from 1 choice
[14716.015262] Initializing USB Mass Storage driver...
[14716.019862] scsi2 : SCSI emulation for USB Mass Storage devices
[14716.020826] usbcore: registered new interface driver usb-storage
[14716.020836] USB Mass Storage support registered.
[14716.022474] usb-storage: device found at 7
[14716.022479] usb-storage: waiting for device to settle before scanning
[14721.020817] usb-storage: device scan complete
[14721.021914] scsi 2:0:0:0: Direct-Access     Crucial  Gizmo!           1100 PQ: 0 ANSI: 0 CCS
[14721.076060] sd 2:0:0:0: [sdb] 3915776 512-byte hardware sectors: (2.00 GB/1.86 GiB)
[14721.077147] sd 2:0:0:0: [sdb] Write Protect is off
[14721.077154] sd 2:0:0:0: [sdb] Mode Sense: 43 00 00 00
[14721.077159] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[14721.079900] sd 2:0:0:0: [sdb] 3915776 512-byte hardware sectors: (2.00 GB/1.86 GiB)
[14721.082650] sd 2:0:0:0: [sdb] Write Protect is off
[14721.082657] sd 2:0:0:0: [sdb] Mode Sense: 43 00 00 00
[14721.082662] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[14721.082674]  sdb: sdb1
[14721.085256] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[14721.085383] sd 2:0:0:0: Attached scsi generic sg2 type 0
[14785.429845] usb 1-4: USB disconnect, address 7
steve@steve-laptop:~$ 
steve@steve-laptop:~$ 
```As you can see there are errors with fwcutter but wireless works.   ???

---

