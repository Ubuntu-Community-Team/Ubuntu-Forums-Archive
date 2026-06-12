---
title: "Getting Epson Stylus TX550W Wi-Fi Scanner Working"
date: 2010-06-22
forum: Networking &amp; Wireless
---

### Post by ..::| Dave89 |::.. on 2010-06-22
We recently got an Epson Stylus TX550W Printer/Scanner unit, shared over Wi-Fi with both Windows/Ubuntu PC's, while I have the printing working flawlessly, I don't know where to start to get the scanner working.  I've Googled, but haven't come up with much, checked the Ubuntu documentation, apparently Ubuntu (9.10 & earlier, nothing about 10.04) don't automatically detect networked printers, is there a way to get it to recognize without editing config files, which I hate doing?  Any help is appreciated, I'm using Ubuntu 10.04 64-bit.

---

### Post by coskierken on 2010-06-22
As far as I have found out, network scanning is not supported.  I have an epson 700 all in one with wireless and can share the printer as you do.  I looked all over the place, also, but have found nothing.  The only options for me was to manually scan to a memory device in the memory card reader in the printer and have it shared or just bring it to my other computer or scan it on one and then share that directory where I scanned it to.  It was even a pain getting the scanner to work on the main system as I had to hook up the usb cable to it for the scanner to be recongized and then put in the right usb code in the epson.config file for the scanner to even work.  Good Luck!

---

### Post by ..::| Dave89 |::.. on 2010-06-23
I've tried scanning to my laptop, directly connected via USB, the LCD on the printer/scanner says something like failed connection.  If I load up Simple Scan, and click scan, it appears to be scanning for a few sceconds, then comes up with something like connection failed.  Scanner/printer also doesn't appear to support scanning directly to memory card or USB stick, which would have been enough for me.

---

### Post by jgaines on 2010-06-25
Not sure about the direct connection, but I've got my TX550W scanning just fine over the network.  You need to install the iscan and iscan-network-nt packages from avasys.  Then you just put the IP address of your TX550W into a config file.  See [this page]("http://ubuntuforums.org/showthread.php?t=1515687") for more details.

---

