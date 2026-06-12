---
title: "Need help with capture card (HVR-1250) can not open"
date: 2009-09-18
forum: Mythbuntu
---

### Post by yzfr1 on 2009-09-18
Ok everyone.  Please forgive me.  I have been working on this for a week.  I love a challenge but after scouring through pages, manuals, wikis and forum threads I still can't get this working... So I am asking some experts to please help with what I am doing wrong.

I have a Hauppauge HVR-1250 capture card.  I got this for the price and it was suggested from someone that said it worked for them.  Unfortunately this person was just someone I met at work that isn't around anymore.

Anyway, I installed Mythbuntu for the first time and installation went ok.  I have an nvidia geforce 7800 graphics card that I had problems with but figured it out thanks to you guys here.

I, however, have not been able to get my capture card to work.  First off, I have ready many posts and wiki's on how to make it work.

I saw this [post ]("http://ubuntuforums.org/showthread.php?t=1234274&highlight=1250")about recompiling the v4l-dvb drivers. 

I then saw this [post ]("http://ubuntuforums.org/showthread.php?t=1014551")about making sure the card is recognized.  Which it is.

I have been to linuxtv.org and tried the scan feature to make sure this works on this [page]("http://www.linuxtv.org/wiki/index.php/Dvbscan").

Ok..  so here is my issue.  I can't get the mythtv backend to recognize my card.  
I feel just plain dumb.  I go to the setup capture card page and I saw somewhere that the card should be recognized under v4l.  

I am not sure if I am placing the right thing value in the Video Device line.
I have tried 
/dev/dvb/
/dev/dvb/adapter0
/dev/dvb/adapter0/dvr0

I have tried pretty much everything in the /dev/dvb/ folder.

Here are some of my settings..

uname
Linux TIVO-1 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux

lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 10)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7900 GT/GTO] (rev a1)
02:00.0 Ethernet controller: Attansic Technology Corp. L2 100 Mbit Ethernet Adapter (rev a0)
03:00.0 Multimedia video controller: Conexant Systems, Inc. Device 8880 (rev 04)
04:01.0 Network controller: RaLink RT2561/RT61 802.11g PCI

dmsg (snipped)
[    2.174034] registered taskstats version 1
[    2.174119]   Magic number: 9:955:310
[    2.174133] tty tty39: hash matches
[    2.174171] rtc_cmos 00:03: setting system clock to 2009-09-18 03:19:46 UTC (1253243986)
[    2.174174] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.174175] EDD information not available.
[    2.174378] Freeing unused kernel memory: 532k freed
[    2.174467] Write protecting the kernel text: 4116k
[    2.174500] Write protecting the kernel read-only data: 1528k
[    2.656018] usb 4-1: new low speed USB device using uhci_hcd and address 2
[    2.828697] PM: Starting manual resume from disk
[    2.828700] PM: Resume from partition 8:5
[    2.828701] PM: Checking hibernation image.
[    2.828880] PM: Resume from disk failed.
[    2.842952] usb 4-1: configuration #1 chosen from 1 choice
[    2.849576] usbcore: registered new interface driver hiddev
[    2.849642] usbcore: registered new interface driver usbhid
[    2.849644] usbhid: v2.6:USB HID core driver
[    2.859253] kjournald starting.  Commit interval 5 seconds
[    2.859270] EXT3-fs: mounted filesystem with ordered data mode.
[    2.867898] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input3
[    2.868607] logitech 0003:046D:C517.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.2-1/input0
[    2.896685] logitech 0003:046D:C517.0002: fixing up Logitech keyboard report descriptor
[    2.897308] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.1/input/input4
[    2.897411] logitech 0003:046D:C517.0002: input,hiddev96,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.2-1/input1
[    3.915156] udev: starting version 141
[    4.332335] input: PC Speaker as /devices/platform/pcspkr/input/input5
[    4.409431] parport_pc 00:07: reported by Plug and Play ACPI
[    4.409501] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[    4.539215] Linux agpgart interface v0.103
[    4.641768] Atheros(R) L2 Ethernet Driver - version 2.2.3
[    4.641771] Copyright (c) 2007 Atheros Corporation.
[    4.641809] atl2 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.641818] atl2 0000:02:00.0: setting latency timer to 64
[    4.665648] intel_rng: FWH not detected
[    4.699378] ppdev: user-space parallel port driver
[    4.704577] cfg80211: Calling CRDA to update world regulatory domain
[    4.973052] nvidia: module license 'NVIDIA' taints kernel.
[    5.006922] cfg80211: World regulatory domain updated:
[    5.006926]  (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    5.006928]  (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.006930]  (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    5.006931]  (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    5.006933]  (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.006935]  (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.027603] iTCO_vendor_support: vendor-support=0
[    5.038593] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[    5.038743] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0860)
[    5.038803] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[    5.073717] Linux video capture interface: v2.00
[    5.125342] cx23885 driver version 0.0.2 loaded
[    5.125380] cx23885 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    5.125460] CORE cx23885[0]: subsystem: 0070:2211, board: Hauppauge WinTV-HVR1270 [card=18,autodetected]
[    5.244035] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.244041] nvidia 0000:01:00.0: setting latency timer to 64
[    5.244622] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.16  Sat Jan 24 19:42:59 PST 2009
[    5.267217] rt61pci 0000:04:01.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    5.273382] tveeprom 0-0050: Hauppauge model 22111, rev C2F5, serial# 6247647
[    5.273384] tveeprom 0-0050: MAC address is 00-0D-FE-5F-54-DF
[    5.273387] tveeprom 0-0050: tuner model is NXP 18271C2 (idx 155, type 54)
[    5.273389] tveeprom 0-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[    5.273391] tveeprom 0-0050: audio processor is CX23888 (idx 40)
[    5.273392] tveeprom 0-0050: decoder processor is CX23888 (idx 34)
[    5.273394] tveeprom 0-0050: has no radio, has IR receiver, has no IR transmitter
[    5.273396] cx23885[0]: hauppauge eeprom: model=22111
[    5.273398] cx23885_dvb_register() allocating 1 frontend(s)
[    5.273416] cx23885[0]: cx23885 based dvb card
[    5.274929] phy0: Selected rate control algorithm 'pid'
[    5.331886] Registered led device: rt61pci-phy0:radio
[    5.331901] Registered led device: rt61pci-phy0:assoc
[    5.367851] tda18271 1-0060: creating new instance
[    5.369893] TDA18271HD/C2 detected @ 1-0060
[    5.394693] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.394737] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    5.600688] DVB: registering new adapter (cx23885[0])
[    5.600692] DVB: registering adapter 0 frontend 0 (LG Electronics LGDT3305 VSB/QAM Frontend)...
[    5.601024] cx23885_dev_checkrevision() Hardware revision = 0xd0
[    5.601031] cx23885[0]/0: found at 0000:03:00.0, rev: 4, irq: 17, latency: 0, mmio: 0xfe800000
[    5.601038] cx23885 0000:03:00.0: setting latency timer to 64
[    5.692438] lp0: using parport0 (interrupt-driven).
[    5.893992] Adding 995988k swap on /dev/sda5.  Priority:-1 extents:1 across:995988k
[    6.507847] EXT3 FS on sda1, internal journal
[    7.333958] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[    7.335132] SGI XFS Quota Management subsystem
[    7.375112] XFS mounting filesystem sda6
[    7.532597] Ending clean XFS mount for filesystem: sda6
[    7.994409] type=1505 audit(1253243992.317:2): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2005
[    7.994501] type=1505 audit(1253243992.317:3): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2005
[    7.994534] type=1505 audit(1253243992.317:4): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2005
[    7.994563] type=1505 audit(1253243992.317:5): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2005
[    8.091957] type=1505 audit(1253243992.413:6): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2010
[    8.092104] type=1505 audit(1253243992.417:7): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2010
[    8.112195] type=1505 audit(1253243992.437:8): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=2014
[    8.131960] type=1505 audit(1253243992.453:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2018
[   17.276039] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.276042] Bluetooth: BNEP filters: protocol multicast
[   17.330028] Bridge firewalling registered
[   22.675110] atl2 0000:02:00.0: irq 2300 for MSI/MSI-X
[   22.675323] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.675858] rt61pci 0000:04:01.0: firmware: requesting rt2561s.bin
[   22.813485] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.268045] wlan0: authenticate with AP 00:1c:10:08:28:bc
[   24.269676] wlan0: authenticated
[   24.269678] wlan0: associate with AP 00:1c:10:08:28:bc
[   24.271992] wlan0: RX AssocResp from 00:1c:10:08:28:bc (capab=0x1 status=0 aid=3)
[   24.271996] wlan0: associated
[   24.272938] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   24.273006] wlan0: disassociating by local choice (reason=3)
[   30.744137] wlan0: authenticate with AP 00:1c:f0:55:bd:e3
[   30.745476] wlan0: authenticated
[   30.745482] wlan0: associate with AP 00:1c:f0:55:bd:e3
[   30.752867] wlan0: RX AssocResp from 00:1c:f0:55:bd:e3 (capab=0x431 status=0 aid=2)
[   30.752872] wlan0: associated
[   30.786106] padlock: VIA PadLock not detected.
[   34.464009] wlan0: no IPv6 routers present


Ok..   someone please help me...

What can I do to make this work?

I have read several posts that people say it works..  but I can't figure it out.  I have been staying up late for about a week and it is not making my wife too happy..  lol

All help is much appreciated..  

BTW --  This is a great forum!

---

### Post by bsntech on 2009-09-18
I can't speak correctly on this - but since the card is a DVB card, wouldn't you want to use that when setting it up in the back-end?

Just thinking out loud - but I know on all other cards with the digital tuners, you select the DVB input.

For the analog side of the card, it is possible that it is setup as /dev/video0.  So you may have two entries for this card in the back-end; one for the digital side of the tuner and the second for the analog side of the tuner.

Look on this link and see if it helps you at all.  This is for the HVR-1600 which has separate digital and analog tuners:

[http://www.mythtv.org/wiki/Hauppauge_HVR-1600]("http://www.mythtv.org/wiki/Hauppauge_HVR-1600")

---

### Post by bsntech on 2009-09-18
Also, you may want to look at this page to ensure you have scanned for channels (scroll to the bottom of the page) and then attempt to use your card using mplayer and see if the card is even currently working.  This may also provide you with the location that you need (if needed) to put into the MythTV backend.

[http://http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1250]("http://http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1250")

---

### Post by yzfr1 on 2009-09-18
> **bsntech said:**
> Also, you may want to look at this page to ensure you have scanned for channels (scroll to the bottom of the page) and then attempt to use your card using mplayer and see if the card is even currently working.  This may also provide you with the location that you need (if needed) to put into the MythTV backend.

[http://http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1250](http://http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1250)



Thanks for you quick reply.  I am working on your first post.  I looked for /dev/video0 but do not see that in the /dev directory.  Looking through the hvr-1600 page right now....



Tried the link..  does not work....

---

### Post by bsntech on 2009-09-18
For some reason, that HVR-1250 link added two http:// in front of it - so just take out the extra.

From the HVR-1600 page:

    * Configure the ATSC (digital) half of the card as any other DVB DTV capture card 

   1. Add another tuner card
   2. Under Card type choose 'DVB DTV capture card (v3.x)'.
   3. Choose the correct value under DVB Device Number (usually 0, this should be the same number appended to /dev/video when configuring the analog portion of the card). Starting with 0.22, this field will be a string like: /dev/dvb/adapter0/frontend0. A second card would be /dev/dvb/adapter1/frontend0.
   4. Frontend ID should populate to something like "Samsung S5H1409 QAM/Subtype: ATSC'.
   5. Select Recording Options.
   6. Change Max recordings to 1, since this card can only record one thing at a time.
   7. Select Finish.
   8. Select Finish again. 

----

So maybe try to set the card up using DVB in the back-end and specify /dev/dvb/adapter0/frontend0

---

### Post by yzfr1 on 2009-09-18
> **bsntech said:**
> 

----

So maybe try to set the card up using DVB in the back-end and specify /dev/dvb/adapter0/frontend0


Ok..  I tried adding /dev/dvb/adapter0 in the DVB section of the back-end.  I cannot however, as it will only allow me put a "0" in that space for "DVB Devic Number".

I selected save after this as it shows "Frontend ID: LGDT3305 Subtpe: ATSC".

I when to the input connections section and it says DVB-Input > none

I know my card is working as I can scan channels with scan.

I just don't how to get it working with the back-end.

---

### Post by bsntech on 2009-09-18
Well, I believe there may have been something you have done in the process of setting up this MythBuntu then.

What I would say for you to do is to re-download the newest version of MythBuntu and install it.  Do not do any of the driver updates or anything.  I've seen numerous threads where the HVR-1250 "worked out of the box" with the setup without any tweaking of drivers.

---

### Post by yzfr1 on 2009-09-18
Ok..  well I have installed it so many times now just trying to get my resolution and graphics card working that I will try it again...  

I should have all of the pages bookmarked that I needed to get the graphics card working with nvidia drivers...  took me while as the resolution was all messed up..

I will try that and get post back my results...

also..  one more thing...

I have seen a few places that say the remote does not work with the HVR-1250.  I also found a site for making the remote work or programming buttons for it..  anyone know if it doesn't work, how to get it to work?  or am I just out of luck?

---

### Post by bsntech on 2009-09-18
You should be able to get the remote to work.  I have the same IR receiver and remote for an older PVR-150 and it works fine.  You will need the lircrc file - which has all of the buttons mapped out to key commands for MythTV.  There are many different versions of this file floating around so that is up to you on picking up the file and tweaking it to your needs.

I don't have any off the top of my head, but there are plenty of help guides available to get lirc installed, have it pick up the remote, and then test the remote in a command window and see if the computer is picking up the commands.

While not fully helpful to you, I do have some links that I used to setup my system on my website.  The link below also has a link to the lircrc file I am using if you want to give it a try.

[http://www.bsntech.com/content/view/591/281/]("http://www.bsntech.com/content/view/591/281/")

---

### Post by yzfr1 on 2009-09-18
Ok!  Success..  Got it running!  Thank you bsntech!

I still do not have the remote working or even know how to get it working.  

How can I test to see if my remote is even being picked up by the IR receiver for the card?

---

### Post by bsntech on 2009-09-18
Open a terminal and issue command:

irw

Then start pressing items on your remote.  If it is working, you should start to see some stuff appear.

Use Ctrl+C to then exit out.

---

