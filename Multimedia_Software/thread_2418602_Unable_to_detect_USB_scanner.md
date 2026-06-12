---
title: "Unable to detect USB scanner"
date: 2019-05-08
forum: Multimedia Software
---

### Post by satimis on 2019-05-08
Hi all,

I have another box here running Ubuntu 16.04 as OS
Simple Scan 3.20.0 (I couldn't find XSane on the menu)
GIMP 2.8.16

On Gimp
File -> Create
it shows "XSane" there

But Epson Perfection 3490 flatbed scanner can't be detected

&#10219; lsusb```

Bus 003 Device 003: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 003 Device 002: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 04b8:0122 Seiko Epson Corp. GT-F520/GT-F570 [Perfection 3590 PHOTO]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 05fc:0231 Harman 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

&#10219; scanimage -L```

device `snapscan:libusb:001:004' is a EPSON EPSON Scanner flatbed scanner

```

&#10219; scanimage --help```

......
......
[snapscan] Cannot open firmware file /usr/share/sane/snapscan/your-firmwarefile.bin.
[snapscan] Edit the firmware file entry in snapscan.conf.
scanimage: open of device snapscan:libusb:001:004 failed: Invalid argument
Type ``scanimage --help -d DEVICE'' to get list of all options for DEVICE.

List of available devices:
    snapscan:libusb:001:004

```

Please help.  Thanks

Regards
satimis

---

### Post by Claus7 on 2019-05-09
Hello,

have you installed the necessary firmware? A quick search revealed this:
[http://www.autodidacts.io/how-to-get-epson-perfection-3490-flatbed-scanner-working-on-ubuntu-linux/](http://www.autodidacts.io/how-to-get-epson-perfection-3490-flatbed-scanner-working-on-ubuntu-linux/)
it might be helpful.

Regards!

---

### Post by satimis on 2019-05-09
> **Claus7 said:**
> Hello,

have you installed the necessary firmware? A quick search revealed this:
[http://www.autodidacts.io/how-to-get-epson-perfection-3490-flatbed-scanner-working-on-ubuntu-linux/](http://www.autodidacts.io/how-to-get-epson-perfection-3490-flatbed-scanner-working-on-ubuntu-linux/)
it might be helpful.

Hi,

Ah I forgot to install the firmware.  Now I have fixed my problem.

Thanks

Besides I found VueScan working better than XSane to scan film negatives.  The images are more sharp and clearer.  I have boxes of them to work.

Regards
satimis

---

