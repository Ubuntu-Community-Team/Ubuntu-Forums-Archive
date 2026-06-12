---
title: "X/sane not recognize Microtek X12 USL"
date: 2007-02-08
forum: Multimedia &amp; Video
---

### Post by ThorstenHH on 2007-02-08
Hi All
I connected my  Microtek X12 USL scanner via USB, but is not recognizesd in X/Sane. The syslog show that a device is found.

```
Feb  8 10:56:32 thorsten-linux kernel: [17181922.240000] ohci_hcd 0000:00:02.0: wakeup
Feb  8 10:56:32 thorsten-linux kernel: [17181922.628000] usb 2-1: new full speed USB device using ohci_hcd and address 6
Feb  8 10:56:32 thorsten-linux kernel: [17181922.832000] usb 2-1: configuration #1 chosen from 1 choice
```

and cat /proc/bus/usb/devices shows 
```
T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  6 Spd=12  MxCh= 0
D:  Ver= 1.00 Cls=ff(vend.) Sub=03 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=05da ProdID=20b0 Rev= 0.00
C:* #Ifs= 1 Cfg#= 1 Atr=40 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=00(>ifc ) Sub=00 Prot=00 Driver=(none)
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=   8 Ivl=0ms
E:  Ad=03(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
```


I wonder if the X12 USL sould be supported via USB. Or does  I need to install a additional device driver ?

Thanks a lot 
Thorsten

---

### Post by roboknight on 2007-09-10
I was wondering if anyone else had looked at this problem.  I too have a Microtek 12X USL scanner.  When running sane-find-scanner I get:

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x05da, product=0x20b0) at libusb:001:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

From the scanimage -L results, it appears to *NOT* be supported since it isn't found.  However, I've seen *OLD* references to a patch to the microtek2 sane backend that supported the USB mode of this scanner.  Has anyone else tried this scanner with Feisty?

At any rate, no joy using the scanner so far.

---

