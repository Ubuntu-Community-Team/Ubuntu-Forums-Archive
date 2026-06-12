---
title: "KARMIC-USB Filmscanner - anyone yet got one running?"
date: 2009-10-29
forum: Multimedia Software
---

### Post by emarkay on 2009-10-29
Bus 001 Device 005: ID 05a9:1550 OmniVision Technologies, Inc. VEHO Filmscanner.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Also known as "Vupoint FS-C1-VP", "*VEHO* VFS-001", ans some more generic, this one is just called "Filmscanner".

Main vendors are  here:
[http://www.vupointsolutions.com/FS-C1-VP.asp](http://www.vupointsolutions.com/FS-C1-VP.asp)
[http://www.veho-uk.com/productdetail.aspx?id=31](http://www.veho-uk.com/productdetail.aspx?id=31)
I am almost sure it uses this sensor: 
[http://www.ovt.com/products/ip_detail.php?id=7](http://www.ovt.com/products/ip_detail.php?id=7)

Haven't seen a "yes" or "no" anywhere, and have seen an "almost certain" that it would work with VueScan Scanning Software:
[http://www.hamrick.com/](http://www.hamrick.com/)

But alas, not detected, nor in GIMP, nor inXszne, or IrfanView in WINE, or SANE.
As for the Win Drivers and software, they use ArcSoft Photoimpression and WINE says "no".
[http://appdb.winehq.org/objectManage...sion&iId=17837]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=17837")
Supplied Photomipression is  Version 6.) and there is a 6.5 available:
[http://www.arcsoft.com/estore/softwa...oductCode=PI65]("http://www.arcsoft.com/estore/software_title.asp?ProductCode=PI65")

Also:id

uid=1000(username) gid=1000(username) groups=4(adm),20(dialout),24(cdrom),29(audio),46(p  lugdev),103(fuse),
104(lpadmin),112(netdev),115(admin),122(sambashare  ),1000(username)

And: sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.
  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.
found USB scanner (vendor=0x05a9, product=0x1550) at libusb:001:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.
  # Not checking for parallel port scanners.
  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

And:  dmesg | tail -n15

[   31.608364] CPU1 attaching sched-domain:
[   31.608367]  domain 0: span 0-1 level MC
[   31.608371]   groups: 1 0
[   31.608376]   domain 1: span 0-1 level CPU
[   31.608379]    groups: 0-1 (__cpu_power = 204:cool:
[   35.570200] CPU0 attaching NULL sched-domain.
[   35.570212] CPU1 attaching NULL sched-domain.
[   35.588149] CPU0 attaching sched-domain:
[   35.588156]  domain 0: span 0-1 level CPU
[   35.588161]   groups: 0 1
[   35.588171] CPU1 attaching sched-domain:
[   35.588174]  domain 0: span 0-1 level CPU
[   35.588178]   groups: 1 0
[ 2196.620276] usb 1-3: new high speed USB device using ehci_hcd and address 4
[ 2196.754190] usb 1-3: configuration #1 chosen from 1 choice

Thanks all, any other ideas?

Original (Closed) Karmic thread:
[http://ubuntuforums.org/showthread.php?t=1295571](http://ubuntuforums.org/showthread.php?t=1295571)

---

### Post by beercz on 2009-11-21
Hi

My dad has just bought a usb veho 35mm slide scanner.

Have you got this working?

---

### Post by emarkay on 2009-11-23
Not in Ubuntu, yet.

I am boggled that no one in the Open Source Community scans slides or negatives economically (on the cheap) ...

---

### Post by JDrabik on 2009-11-25
Nothing yet, but this appears very similar to the Innovative Technology (also, from lsusb, "Omnivision Technologies" 35 mm film/slide scanner (FilmScan35 I).  I just purchased one of them and it gives good results on Windows but I can't travel to my friends house just to use a buggy OS.

So, I called the Innovative folks and spoke with tech support.  They tell me they are working on a driver and that it could be ready "in about a month".  Innovative are the same folks who have Linux support for their USB turntable, by the way, so I find the comment both believable and refreshing.

In the meantime, I've experimented with trying to get it recognized as an Epson scanner (it fails), and have generally poked around the device a bit but haven't gotten any deeper than that.  If they don't get a driver out by Christmas, I'll have another look then.

Perhaps if a number of people contact these vendors (be nice) they'll add Linux support.  If folks like Innovative, a relatively small company, can add Linux support in a month then other vendors should be able to do the same.  If we don't ask, they won't write.

---

### Post by Balle-Larsen on 2009-12-14
I have a Envivo scanner with the usb identification string:
05a9:1550 OmniVision Technologies, Inc. VEHO Filmscanner

I wrote to Veho Technical <technical@veho-uk.com>, but unfortunately I got this back.

Unfortunately the Envivo filmscanner is not a Veho product and so we cannot provide technical support on this product. However I can tell you that neither of our scanners are compatible with Linux.

Any suggestions to who I should write and request a driver?

---

### Post by pwabrahams on 2009-12-26
I just got myself a 21c scanner from Ebay. **xsane** doesn't recognize it. **lsusb** shows:
> Bus 002 Device 002: ID 0e8f:0016 GreenAsia Inc.

And kinfocenter shows:
> USB Camera
Manufacturer: FW-07.07.25
Class
0
((Defined at Interface level))
Subclass
0

Protocol
0

USB Version
2.00

Vendor ID
0x5a9
(OmniVision Technologies, Inc.)
Product ID
0x1550

Revision
0.00

Speed
480 Mbit/s

Channels
0

Max. Packet Size
64


Now here's the *really* interesting part.  Here's what I found via Google on forum.nginx.org, which I've never heard of:
> Karl F. Larsen
Re: Scanning Slides and Negatives - Epson 4490 with Linux Driver?
December 22, 2009 05:02PM 	

I have a 21c Film and Slide Digital Converter. It converts
Film and Slides to .jpg files on your computer. The box states
it works Only with windows. As usual if you just plug it into
your Ubuntu it works fine. The drivers needed to make it work
on windows are un-needed by Linux.

I will sell this for $65.00 American dollars plus shipping
cost of unknown amount. If you live outside the USA it might
be expensive.

73 Karl


--

Karl F. Larsen, AKA K5DI
Linux User
#450462 [http://counter.li.org](http://counter.li.org).
Key ID = 3951B48D

Unfortunately Karl doesn't give his email address.

So *someone* got the bugger to work under Ubuntu, but I can't (I'm running Kosmic Koala 9.10).

---

### Post by JayDB on 2010-04-04
Did you ever hear back from innovative about the FilmScan35 driver??? Thx

---

### Post by emarkay on 2010-04-04
ITNS-300 35mm Negative Film &  Slide Scanner

[http://www.ithomeproducts.com/product/35mm-negative-film-slide-scanner](http://www.ithomeproducts.com/product/35mm-negative-film-slide-scanner)


**Innovative Technology**
4  Anchor Way
Port Washington, NY 11050
 **Phone: **877.ITECH97  (877.483.2497) 
 **E-mail:** [EMAIL="support@ithomeproducts.com"]support@ithomeproducts.com[/EMAIL]

[http://www.ithomeproducts.com/support](http://www.ithomeproducts.com/support)

Testing Lucid now, but nothing new - will also email 
**Innovative Technology.**

---

### Post by Ken N on 2010-08-10
Hi **Problem Solved** I have just bought the Veho VFS_002m initially I could only get it to work on WinXP using the provided software. However the way it worked reminded me of the cheese webcam application and have since tried it and it works just great. I would say that it gives better results than the provided software.

I hope this is of help
Ken N

---

### Post by fussl on 2010-10-20
> **Ken N said:**
> Hi **Problem Solved** I have just bought the Veho VFS_002m initially I could only get it to work on WinXP using the provided software. However the way it worked reminded me of the cheese webcam application and have since tried it and it works just great. I would say that it gives better results than the provided software.

I hope this is of help
Ken N
What did you do to get it running? I cannot get anything out of the damned thing!

---

### Post by bluekarasu on 2010-10-21
I have a film scanner called "Vistaquest FS-500-1 "  lsusb : ID 05a9:1550 OmniVision Technologies, Inc. VEHO Filmscanner

I can't use it under Ubuntu (nor with win7, buggy driver) I've tried Xsane, simple scan or cheese.

Ken N, can you explain what you have done to get it work? What is the lsusb id of your product?

---

### Post by TheCrook on 2011-08-06
> **fussl said:**
> What did you do to get it running? I cannot get anything out of the damned thing!

I have found two ways to get it working.

[LIST]
[*]Install cheese (either synaptic or from the command line with "sudo apt-get install cheese"
[*]before starting cheese connect yur scanner to a USB port
[*]start cheese and you should see a picture
[*]the alternative is to install streamer (e.g. sudo apt-get install streamer)
[*]once you have done that you can scan pictures from the command line with this command: streamer -f jpeg -o /path/to/image.jpeg
[/LIST]

I get the best quality initial scan with cheese but you can always use GIMP to improve your images afterwards.

Who needs Windows with yet another being loaded all the time.

:)

---

### Post by kokito on 2011-08-22
still not working for me (on natty)!  :confused: 

```
jumba@jumba:/$ streamer -f jpeg -o ~/Scrivania/immagine.jpg
dlopen: /usr/lib/xawtv/flt-disor.so: undefined symbol: tan
dlopen: /usr/lib/xawtv/flt-gamma.so: undefined symbol: pow
neither audio nor video format specified/found
jumba@jumba:/$ 

```

cheese doesn't recognise it at all...

any other workaround?
thanks!

---

### Post by whitegecko on 2013-03-18
Maybe its an issue of udev or hal or something like that.

---

### Post by oldos2er on 2013-03-18
Old thread closed, please don't bump old threads.

---

