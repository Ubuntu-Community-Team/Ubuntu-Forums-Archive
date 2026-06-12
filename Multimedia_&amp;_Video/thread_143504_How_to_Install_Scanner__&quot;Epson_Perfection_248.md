---
title: "How to Install Scanner  &quot;Epson Perfection 2480&quot; ?"
date: 2006-03-12
forum: Multimedia &amp; Video
---

### Post by patrick295767 on 2006-03-12
1/
First, I would recommand you to check /etc/apt/sources.list
with my :
[breezy]("http://patrick295767.sitesled.com/miniram/sources.list-breezy") [dapper]("http://patrick295767.sitesled.com/miniram/sources.list-dapper") [edgy]("http://patrick295767.sitesled.com/miniram/sources.list-edgy")
 
2/ you have to make sure the xsane and sane are successfully installed
  
check below my automatic script !!
 
3/ unplug epson 2480
4/ plug epson 2480
5/ sudo lsusb
 check you can see EPSON sthg written
6/ are user type: scanimage -L
 note down the number of device
7/ start gimp and select this number of device

---

### Post by Rollmops on 2006-03-12
Probably, you need to configure the driver to use the correct firmware for your scanner. Look here for more info: [http://snapscan.sourceforge.net/](http://snapscan.sourceforge.net/)

---

### Post by patrick295767 on 2006-03-26
I downloaded the sane backend 0.17, unpacked it ...
ok

Please what should I do now ?

=======
./configure
make 
make install 

done 
==========
I changed my file   epson.conf 
in /etc 
(with vendor product)
done
  =======
  
tools/find-scanner is not found ??
  where to find it ? where/ how to konw which /dev/...??? is my scanner in order to do : 
what said in sane backend : 
> 
	
SnapScan Backend for SANE

This page provides information on the SnapScan Backend for SANE. This driver is compatible with a wide range of scanners from Afga, Acer, Benq, Vuego, Epson, Guillemot, Hercules and Mitsubishi.

Agfa has released the specs for their older SCSI scanner models. Other vendors have released no specs at all, so it is usually not possible to support all features of every scanner.

We used information provided by many existing web site to try to create an exhaustive page. Thanks to the original authors.

If you're looking for Windows drivers for your scanner please contact the vendors (Agfa, Acer / Benq, Epson) of your scanner directly. Please don't send me emails relating to Windows drivers.
News

    * 11/27/05: Benq 5000 (USB Id 0x04a5, 0x20f8) now working
    * 11/13/05: 16 bit support for Epson 2480 and 3490 added
    * 08/16/05: Added support for Epson 3490/3590
    * 02/09/04: Added support for Epson 2480 / 2580
    * 01/12/04: Added support for Epson 1270

Supported Scanners
Here is a list of scanners that have at least worked at one time in the past. I'd like to complete this list, so if you own one of the scanners below and there's a blank field, please send me a mail .

Benq (formerly known as Acer Peripherals) sell their scanners under a number of names, e.g. Vuego, Scan2Web, ScanPrisa and possibly others. The important part of the model name is the number which you'll find in the table below.

Parallel port scanners by Agfa use an unknown protocol for communication. There are currently no plans to support these scanners.

If you own a SCSI or USB scanner form Acer, Benq or Agfa which is not listed on this page and you're willing to run some tests, please send me a mail.
 
 
Vendor
	
Model
	
Bus
	
USB ID
	
ID String 
(after firmware upload)
	
Firmware file
	
Remarks
Acer / Benq 	300f 	SCSI 	- 	"ACERSCAN_A4____1" 	- 	 
Acer / Benq 	310s 	SCSI 	- 	"FlatbedScanner_2" 	- 	 
Acer / Benq 	610s 	SCSI 	- 	"FlatbedScanner_4" 	- 	 
Acer / Benq 	620S 	SCSI 	- 	"FlatbedScanner_9"
	- 	 
Acer / Benq 	620ST 	SCSI 	- 	"FlatbedScanner_9"
"FlatbedScanner17" 	- 	Transparency adapter supported
Acer / Benq 	620+ 	SCSI 	- 	?
	- 	 
Acer / Benq 	640s 	SCSI 	- 	"FlatbedScanner18" 	- 	 
Acer / Benq
	310U
	USB
	0x04a5, 0x1a20
	"FlatbedScanner_5"
	u34v110.bin
	
Acer / Benq 	320U 	USB 	0x04a5, 0x2022
	"FlatbedScanner13"
	u34v110.bin 	 
Acer / Benq 	340U 	USB 	0x04a5, 0x2022
	"FlatbedScanner13" 	u34v110.bin
	 
Acer / Benq 	620U 	USB 	0x04a5, 0x1a2a
0x04a5, 0x2040 	"FlatbedScanner_5"
?
	-
u96v121.bin 	 
Acer / Benq 	620UT 	USB 	0x04a5, 0x2040 	"FlatbedScanner16" 	u64v120.bin 	Transparency adapter supported
Acer / Benq 	640U 	USB 	0x04a5, 0x2060 	"FlatbedScanner20" 	u96v121.bin 	 
Acer / Benq 	640UT 	USB 	?
	?
	u64v120.bin 	Transparency adapter supported
Acer / Benq 	640BU 	USB 	0x04a5, 0x207e 	"FlatbedScanner13"
	u126v043.bin
	 
Acer / Benq 	640BT
	USB
	0x04a5, 0x20be
	"FlatbedScanner20"
	u190v044.bin
	Transparency adapter supported
Acer / Benq 	1240 	USB 	0x04a5, 0x20c0 	"FlatbedScanner19" 	u192v074.bin 	 
Acer / Benq
	3300 / 4300
	USB
	0x04a5, 0x20b0
	"FlatbedScanner23"
	u176v046.bin
	
Acer / Benq 	3300 / 4300 	USB 	0x04a5, 0x20de
	"FlatbedScanner21"
"FlatbedScanner22"
	u222v067.bin
	 
Benq
	5000E
	USB
	0x04a5, 0x20fc
	"FlatbedScanner25"
	u252v065.bin
	Working up to 600 DPI
Benq
	5000U
	USB
	0x04a5, 0x20fc
	"FlatbedScanner25"
	20FCV112.bin
	Same as 5000E?
Benq
	5000
	USB
	0x04a5, 0x20f8
	"FlatbedScanner42"
	20F8V116.bin
	Requires sane-backends 1.0.16 or later
Benq 	5300 	USB 	0x04a5, 0x20fe
	"FlatbedScanner24" 	u254v042.bin
	Problems with firmware upload reported
Agfa 	SnapScan 300 	SCSI 	- 	"SNAPSCAN 300" 	- 	 
Agfa 	SnapScan 310s 	SCSI 	- 	"SNAPSCAN 310" 	- 	 
Agfa 	SnapScan 600 	SCSI 	- 	"SNAPSCAN 600" 	- 	 
Agfa 	SnapScan 1236s 	SCSI 	- 	"SNAPSCAN 1236" 	- 	 
Agfa 	SnapScan 1236u 	USB 	0x06bd, 0x0002 	"SNAPSCAN 1236U" 	?
	 
Agfa 	SnapScan 1212U 	USB 	0x06bd, 0x0001
0x06bd, 0x2061 	"SNAPSCAN 1212U"
"SNAPSCAN 1212U_2" 	not necessary(?)
Snapscan 1212U_2.bin 	
Remove spaces from firmware filename!
Agfa
	SnapScan e10
	USB
	0x06bd, 0x2093
	"SNAPSCAN e10"
	snape10.bin
	 
Agfa 	SnapScan e20 	USB 	0x06bd, 0x2091 	"SNAPSCAN e20" 	Snapscan e20.bin 	Remove spaces from firmware filename!
Agfa 	SnapScan e25 	USB 	0x06bd, 0x2095 	"SNAPSCAN e25" 	snape25.bin 	 
Agfa 	SnapScan e26 	USB 	0x06bd, 0x2097 	"SNAPSCAN e26" 	snape26.bin 	Some models don't need firmware upload
Agfa 	SnapScan e40 	USB 	0x06bd, 0x208d 	"SNAPSCAN e40" 	snape40.bin 	 
Agfa 	SnapScan e42 	USB 	0x06bd, 0x20ff 	"SNAPSCAN e42" 	snape42.bin 	quality calibration not working as specified
Agfa 	SnapScan e50 	USB 	0x06bd, 0x208f 	"SNAPSCAN e50" 	snape50.bin 	 
Agfa 	SnapScan e52 	USB 	0x06bd, 0x20fd 	"SNAPSCAN e52" 	snape52.bin 	quality calibration not working as specified
Agfa
	Arcus 1200
	SCSI
	-
	"Arcus1200"
	-
	 
Epson
	Perfection 660
	USB
	0x04b8, 0x0114
	"Perfection 660"
	tail_058.bin
	Some models don't need firmware upload
Epson
	Perfection 1270
	USB
	0x04b8, 0x0120
	"Epson Scanner1"
	esfw3e.bin
	Added in SANE-backends-1.0.15-CVS
Epson
	Perfection 1670
	USB
	0x04b8, 0x011f
	"Epson Scanner"
	esfw30.bin
	Added in SANE-backends-1.0.13
Epson 	Perfection 2480
	USB
	0x04b8, 0x0121
	"Epson Scanner1" 	esfw41.bin
	Added in SANE-backends-1.0.14-CVS
Needs firmware version > 1.16 (Oct 28 2004) to make transparency adapter work
Epson 	Perfection 2580
	USB
	0x04b8, 0x0121
	"Epson Scanner1" 	esfw41.bin
	Problems reported, solution pending
Epson
	Perfection 3490
	USB
	0x04b8, 0x0122
	"Epson Scanner2"
	esfw52.bin
	added in SANE-backends-1.0.16-CVS
Epson
	Perfection 3590
	USB
	0x04b8, ???
	"Epson Scanner2"
	?
	unested, added in SANE-backends-1.0.16-CVS
Guillemot / Hercules 	MaxiScan A4 Deluxe 	SCSI 	 
	"FlatbedScanner_9" 	-
	Relabeled Acer 620S
Guillemot / Hercules
	Scan @home Touch 1248
	USB
	0x04a5, 0x20de
	"FlatbedScanner21"
	u222v064.bin
	Relabeled Acer 3300
Guillemot / Hercules
	Maxi A4 36bit
	USB
	0x04a5, 0x2060
	"FlatbedScanner20"
	u96v121.bin
	Relabeled Benq 620U, needs firmware from Benq
Mitsubishi
	Diamondview 648UT
	USB
	?
	"FlatbedScanner13"
	?
	Relabeled Acer 320
Mitsubishi
	Diamondview 650U
	USB
	0x04a5, 0x20b0
	"FlatbedScanner23"
	u176v042.bin
	Relabeled Acer 4300

Note:  The Agfa SnapScan Touch uses a different protocol and will not be supported by the Snapscan backend. It may possibly be supported by the HP3300 backend (see the SourceForge  project and Bertrik Sikkens  homepage for more information.
Getting it working
Get the latest version of SANE from the SANE homepage. Development of the SnapScan backend is now done in SANE CVS, so there's no need to download a separate source package for the backend anymore.

To correctly install your scanner, you should 

   1. detect your scanner device

machine# tools/find-scanner
   find-scanner: found scanner "AGFA SNAPSCAN 310 1.20" at device
   /dev/XXXXX 

   2. if you want your scanner to be recognized easily, create a link. For SCSI scanners use:

machine# ln -s /dev/XXXXX /dev/scanner

      For USB scanners use:

machine# ln -s /dev/XXXXX /dev/usbscanner

How to install libusb ??
  xscanimage and nothg ... 
  
xsane says that no usb scanner found ...
thx

---

### Post by phetre on 2006-03-28
Hi, Patrick.  I had a similar problem under Breezy, and got it to work by following these steps:  [http://ubuntuforums.org/showthread.php?t=26911]("http://ubuntuforums.org/showthread.php?t=26911")
I hope this still works for you, with the changes you have made to your system.
Unfortunately, it doesn't seem to work under Dapper (Flight 5).  XSane detects the scanner, but it locks up when I hit "Preview."  Under Gimp, the scanner goes through the motions, but no image appears.  I'd appreciate any help.

---

### Post by patrick295767 on 2006-07-19
To install the epson 2480 wihtout efforts : 

run my script as root, 
  
Enjoy !

easypatrickinstall_epson2480ubuntu.sh
```
#########for the scanner
if [ ! -e /etc/sane.d/esfw41.bin ] ; then
	#################### Scanner Epson 2480
	# mofify the conf in /etc
	apt-get -y -f install sane
	apt-get -y -f install xsane
	apt-get -y -f install xsane-utils
	apt-get -y -f install libusb-dev
	apt-get -y -f install xscanimage
	apt-get -y -f install kooka
	#./configure
	#make 
	#make install
	apt-get -f -y install libsane-extras
	mkdir /tmp
	cd /tmp
	# firmware
	wget -N http://patrick295767.sitesled.com/miniram/esfw41.bin
	wget http://luc.byhet.free.fr/epson2480/esfw41.bin
	cp esfw41.bin "/etc/sane.d/esfw41.bin"
	# now the conf file
	wget -N http://patrick295767.sitesled.com/miniram/snapscan.conf
	cp "snapscan.conf" "/etc/sane.d/snapscan.conf"
fi


```

Nothing else to do, your scanner will be installed.
To check it, type: 
xsane
  
(you can also type for permissions: 
```
sudo chmod 777 -R /proc/bus/usb 
``` )

==
Enjoy Linux

---

### Post by Pjotr123 on 2006-07-28
Patrick, your script works perfectly for me! Thank you very much. Now I can use my scanner as I can in Windows.

Ik ben er heel erg blij mee.

Salut, Pjotr.

---

### Post by patrick295767 on 2006-08-02
> **Pjotr123 said:**
> Patrick, your script works perfectly for me! Thank you very much. Now I can use my scanner as I can in Windows.

Ik ben er heel erg blij mee.

Salut, Pjotr.

You're welcome; Glad this script helped you !

---

### Post by elpuerco on 2006-09-16
Tip Top =D> 

Works a treat thanks a million =D>

---

### Post by kpictjl on 2006-10-01
Patrick, I ran the script and it seemed to finish fine.  No obvious errors.  When I ran xsane I got a "no devices available" dialog box. I feel like I'm missing something obvious.

How do I now tell the scanner to, um, "start scanning?"  In WXP is would just hit the button on the scanner.

Thanks.

---

### Post by osaeris on 2006-10-07
Thanks for this. Worked a treat. Just scanned 80 35mm slides at 2400dpi !!

---

### Post by kpictjl on 2006-11-23
I think I'm missing still missing something fundamental...please help!!

I get these errors when I try to apt-get this package?  Edubuntu Edgy...

E: Couldn't find package xscanimage

Actually, my problem goes a little deeper.  My syslog show this when I plug in the Epson Perfection 2480 Photo usb scanner.
```
Nov 23 23:13:19 pacman kernel: [17183120.824000] usb 2-2: new full speed USB device using uhci_hcd and address 12
Nov 23 23:13:23 pacman kernel: [17183123.936000] usb 2-2: device descriptor read/64, error -110
Nov 23 23:13:38 pacman kernel: [17183139.152000] usb 2-2: device descriptor read/64, error -110
Nov 23 23:13:38 pacman kernel: [17183139.368000] usb 2-2: new full speed USB device using uhci_hcd and address 13
Nov 23 23:13:41 pacman kernel: [17183142.480000] usb 2-2: device descriptor read/64, error -110
Nov 23 23:13:56 pacman kernel: [17183157.696000] usb 2-2: device descriptor read/64, error -110
Nov 23 23:13:57 pacman kernel: [17183157.912000] usb 2-2: new full speed USB device using uhci_hcd and address 14
Nov 23 23:14:02 pacman kernel: [17183162.932000] usb 2-2: device descriptor read/8, error -110
Nov 23 23:14:07 pacman kernel: [17183168.052000] usb 2-2: device descriptor read/8, error -110
Nov 23 23:14:07 pacman kernel: [17183168.268000] usb 2-2: new full speed USB device using uhci_hcd and address 15
Nov 23 23:14:12 pacman kernel: [17183173.288000] usb 2-2: device descriptor read/8, error -110
Nov 23 23:14:17 pacman kernel: [17183178.408000] usb 2-2: device descriptor read/8, error -1
```

---

### Post by kpictjl on 2006-11-23
How about this...is there a difference between "Epson Perfection 2480 Photo" and simply "Epson Perfection 2480"?

---

### Post by patrick295767 on 2006-11-28
> **kpictjl said:**
> How about this...is there a difference between "Epson Perfection 2480 Photo" and simply "Epson Perfection 2480"?

```


#### for scanning

	apt-get -y -f --allow-unauthenticated  install  libsane 
	apt-get -y -f --allow-unauthenticated  install sane 
	apt-get -y -f --allow-unauthenticated  install sane-utils

	apt-get -y -f --allow-unauthenticated  install sane
	apt-get -y -f --allow-unauthenticated  install xsane
	apt-get -y -f --allow-unauthenticated  install xsane-utils
	apt-get -y -f --allow-unauthenticated install libusb-dev
	apt-get -y -f --allow-unauthenticated install scanimage
	apt-get -y -f --allow-unauthenticated install libsane
	apt-get -y -f --allow-unauthenticated install sane-utils
	apt-get -y -f --allow-unauthenticated install scanimage	
	apt-get -y -f --allow-unauthenticated install xscanimage
	apt-get -y -f --allow-unauthenticated install kooka
	apt-get -y -f --allow-unauthenticated install ocrad




#########for the scanner


	#################### Scanner Epson
	# mofify the conf in /etc
	## u have to go into acquire, then, go in XSANE and DEVICE DIALOG


	apt-get -y -f --allow-unauthenticated  install  libsane 
	apt-get -y -f --allow-unauthenticated  et -N http://patrick295767.sitesled.com/miniram/esfw41.bin
	wget http://luc.byhet.free.fr/epson2480/esfw41.bin
	cp /home/winwoinstall sane 
	apt-get -y -f --allow-unauthenticated  install sane-utils

	apt-get -y -f --allow-unauthenticated  install sane
	apt-get -y -f --allow-unauthenticated  install xsane
	apt-get -y -f --allow-unauthenticated  install xsane-utils
	apt-get -y -f --allow-unauthenticated install libusb-dev
	apt-get -y -f --allow-unauthenticated install scanimage
	apt-get -y -f --allow-unauthenticated install libsane
	apt-get -y -f --allow-unauthenticated install sane-utils
	apt-get -y -f --allow-unauthenticated install xscanimage
	apt-get -y -f --allow-unauthenticated install kooka
apt-get -f -y  --allow-unauthenticated  install mc
apt-get -f -y  --allow-unauthenticated  install lynx



	apt-get -f -y  --allow-unauthenticated  install libsane-extras
	mkdir /tmp
	cd /tmp
	# firmware
	wget -N http://patrick295767.sitesled.com/miniram/esfw41.bin
	wget http://luc.byhet.free.fr/epson2480/esfw41.bin
	
	cp esfw41.bin "/etc/sane.d/esfw41.bin"
	# now the conf file
	
	wget -N http://patrick295767.sitesled.com/miniram/snapscan.conf
	cp "snapscan.conf" "/etc/sane.d/snapscan.conf"

```

I used sthg like this. Once it is done it should be ready to go.

Now, you need to use the tricks. it can hang at that time.
not so easy:

I found out it is better to do the scanimage -L as user
and try with gimp and acquire and select the right one (one of them 2)
I will look (dont recall)

---

### Post by kpictjl on 2006-11-28
What is acquire?
> ## u have to go into acquire, then, go in XSANE and DEVICE DIALOG

It still can't find xsane-utils, scanimage or xscanimage.
```

~$ sudo apt-get -y -f --allow-unauthenticated  install xsane-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xsane-utils
~$ sudo apt-get -y -f --allow-unauthenticated install scanimage
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package scanimage
:~$ sudo apt-get -y -f --allow-unauthenticated install xscanimage
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xscanimage

```

Also, scanimage doesn't even find my scanner...
```

:~$ scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
bighead@pacman:~$ sane-find-scanner 

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.
  # Also you need support for SCSI Generic (sg) in your operating system.
  # If using Linux, try "modprobe sg".

  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

```

---

### Post by patrick295767 on 2006-12-01
> **kpictjl said:**
> What is acquire?


It still can't find xsane-utils, scanimage or xscanimage.
```

~$ sudo apt-get -y -f --allow-unauthenticated  install xsane-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xsane-utils
~$ sudo apt-get -y -f --allow-unauthenticated install scanimage
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package scanimage
:~$ sudo apt-get -y -f --allow-unauthenticated install xscanimage
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xscanimage

```

Also, scanimage doesn't even find my scanner...
```

:~$ scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
bighead@pacman:~$ sane-find-scanner 

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.
  # Also you need support for SCSI Generic (sg) in your operating system.
  # If using Linux, try "modprobe sg".

  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

```
Ill look during weekend

---

### Post by patrick295767 on 2006-12-06
1/
First, I would recommand you to check /etc/apt/sources.list
with my :
[breezy]("http://patrick295767.sitesled.com/miniram/sources.list-breezy") [dapper]("http://patrick295767.sitesled.com/miniram/sources.list-dapper") [edgy]("http://patrick295767.sitesled.com/miniram/sources.list-edgy")   then type : sudo apt-get update 
 
2/ you have to make sure the xsane and sane are successfully installed
3/ unplug epson 2480
4/ plug epson 2480
5/ sudo lsusb
 check you can see EPSON sthg written
6/ are user type: scanimage -L
 note down the number of device
example: 'snapscan:libusb:001:008'
7/ start gimp and select this number of device to scan 
  
  
you can also use my script:

  run this command for example 'snapscan:libusb:001:008':
xterm &
sh patrickscript2480.sh 'snapscan:libusb:001:008'
# should be scanned now... 
  
with having this script in ur directory: patrickscript2480.sh
> #!/bin/sh
# patrickscript2480.sh
echo "--- Scanning ... ---"
filename_default="scanned_$(date)"
filetiff="$(echo $filename_default).tiff"
filejpeg="$(echo $filename_default).jpg"
echo "$filetiff" 
echo "$filejpeg"
## this makes a 300 DPI tiff file
xmessage "Scanning ..." &
#scanimage --mode color --format tiff  > "$filetiff"
#scanimage -d 'snapscan:libusb:001:008'   --mode color --format tiff  > "$filetiff"
scanimage -d "$1"   --mode color --format tiff  > "$filetiff"
convert "$filetiff"  "$filejpeg"
rm -rf "$filetiff" 
echo "The file: $(echo $filejpeg) has just been scanned."
echo "--- --- "
## need NTP support 


I didnt fully finish script but it should work
I had to use sed still
no time 

I hope I helped you

---

### Post by kpictjl on 2006-12-14
I'm not sure exactly what happened buy now my scanner works.  It has to do with the exact procedure for connecting the cables to the scanner.

The MS Windows install procedure that comes with the scanner says...
1) install software onto PC (this doesn't apply to linux)
2) connect usb cable
3) connect power cable to scanner
4) reboot

I recommend that if you are chasing your tailhttp://ubuntuforums.org/images/smilies/eusa_wall.gif trying to make ubuntu recognize this scanner, then try steps 2-4 above and see how it goes.

Good luck

---

### Post by matchstich on 2006-12-15
ok, i went to
[http://snapscan.sourceforge.net/](http://snapscan.sourceforge.net/) scrolled down to where the intructions for libusb are, so, 
it say i am to load this ---modprobe  scanner vendor=0xVVVV product=0xPPPP--, cept i dont know what to put in for vendor # or product#
also, i have the firmware in a folder on my deskstop, how do i get it in whereever it needs to be. thanks

i am trying to get acer 620u installed

---

### Post by patrick295767 on 2006-12-23
this scanner in linux, It is working very very great ... better than in Windows for me
and cool automatic scanning-script ;  hehe
  
Try to add me in ur buddy list of gaim, I can help you in Realtime, .... 
you should not buy anohter scanner maybe just because you cannot instlal it... i guess

---

### Post by christopherberry11 on 2006-12-28
No longer a prob!

---

### Post by johntelthorst on 2007-06-12
Thanks for a good script, it worked for me after I edited a line in /etc/sane.d/snapscan.conf to read

```
firmware /etc/sane.d/esfw41.bin
```

 and manually installed xsane utilities.  Thanks for the script.

---

### Post by vgrisham on 2007-06-22
Patrick, et. al.,

Where is this script described in the thread? I'm trying to get my Epson 2580 rolling with Feisty (it worked fine in Dapper).

Thanks,
Vaughn

---

### Post by patrick295767 on 2007-08-26
> **vgrisham said:**
> Patrick, et. al.,

Where is this script described in the thread? I'm trying to get my Epson 2580 rolling with Feisty (it worked fine in Dapper).

Thanks,
Vaughn

webhosting down again

#################### Scanner Epson
	# mofify the conf in /etc
	apt-get -y -f install sane
	apt-get -y -f install xsane
	apt-get -y -f install xsane-utils
	apt-get -y -f install libusb-dev
	apt-get -y -f install scanimage
	apt-get -y -f install libsane
	apt-get -y -f install sane-utils
	apt-get -y -f install xscanimage
	apt-get -y -f install kooka
	#./configure
	#make 
	#make install
	apt-get -f -y  --allow-unauthenticated  install libsane-extras
	mkdir /tmp
	cd /tmp
	# firmware
	#wget -N [http://patrick295767.sitesled.com/miniram/esfw41.bin](http://patrick295767.sitesled.com/miniram/esfw41.bin)
	wget [http://luc.byhet.free.fr/epson2480/esfw41.bin](http://luc.byhet.free.fr/epson2480/esfw41.bin)
	cp esfw41.bin "/etc/sane.d/esfw41.bin"
	# now the conf file
	# wget -N [http://patrick295767.sitesled.com/miniram/snapscan.conf](http://patrick295767.sitesled.com/miniram/snapscan.conf)
	cp "/dffddsfdsffddsfdfnapscan.conf"  "/etc/sane.d/snapscan.conf"

---

### Post by changlinn on 2007-09-23
I ran your script Patrick and it got most of the way through but failed getting the snapscan.conf, I checked it and set the firmware to the bin file, but no luck, scanimage -L doesn't find anything.
can someone just post the snapscan.conf or mail it to me and I will mirror it.

---

### Post by changlinn on 2007-09-23
oh well that was easy, I just had to put in to the snapscan.conf
firmware /path/to/efsw410.bin

Reboot and all was good.

---

### Post by patrick295767 on 2007-10-17
> **changlinn said:**
> oh well that was easy, I just had to put in to the snapscan.conf
firmware /path/to/efsw410.bin

Reboot and all was good.

I just made a mirror here of the files:
[http://patrick295767.pa.funpic.org/EpsonPerfection2480/](http://patrick295767.pa.funpic.org/EpsonPerfection2480/)

Best regards

---

