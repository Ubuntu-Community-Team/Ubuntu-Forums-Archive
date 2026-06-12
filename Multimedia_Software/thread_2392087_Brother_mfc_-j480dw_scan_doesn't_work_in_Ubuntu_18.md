---
title: "Brother mfc -j480dw scan doesn't work in Ubuntu 18.04"
date: 2018-05-16
forum: Multimedia Software
---

### Post by markus51 on 2018-05-16
Hi, sorry for my english cause i'm italian.
I turned on the printer connected via usb. Ubuntu has automatically loaded a generic driver (but told me not to provide for the scanner function).
Still with the printer on, I went into settings and removed the printer.
I downloaded the "driver install tool" in home.
I moved on the home.
I followed the installation instruction for "driver install tool".
At the end of the installation process, the printer works well but the simple scan doesn't detect the scanner.
I've done a fresh Ubuntu 18.04 installation in hard disk.
The following commands try to help you in solving this problem

```
marco@marcopc:~$  dpkg -l | grep -i Brother
ii  brscan-skey                                0.2.4-1                             amd64        Brother Linux scanner S-KEY tool
ii  mfcj480dwcupswrapper:i386                  1.0.0-0                             i386         Brother Inkjet printer CUPS Driver 
ii  mfcj480dwlpr:i386                          1.0.0-0                             i386         Brother inkjet lpr printer Driver 
ii  printer-driver-brlaser                     4-1                                 amd64        printer driver for (some) Brother laser printers
ii  printer-driver-ptouch                      1.4.2-3                             amd64        printer driver Brother P-touch label printers
marco@marcopc:~$ 

```

```
marco@marcopc:~$ lsusb; sane-find-scanner; scanimage -L
Bus 002 Device 003: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

could not open USB device 0x045e/0x0745 at 002:003: Access denied (insufficient permissions)
could not open USB device 0x8087/0x0024 at 002:002: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 002:001: Access denied (insufficient permissions)
could not open USB device 0x8087/0x0024 at 001:002: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 001:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0003 at 004:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 003:001: Access denied (insufficient permissions)
  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
marco@marcopc:~$ 

```


```
marco@marcopc:~$ sudo sane-find-scanner
[sudo] password di marco: 

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
marco@marcopc:~$ 

```

```
marco@marcopc:~$ scanimage -Lmarco@marcopc:~$ scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
marco@marcopc:~$ 


No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
marco@marcopc:~$ 

```

---

### Post by kurt18947 on 2018-05-17
Are you aware of this page?

[http://support.brother.com/g/s/id/linux/en/index.html?c=us_ot&lang=en&comple=on&redirect=on](http://support.brother.com/g/s/id/linux/en/index.html?c=us_ot&lang=en&comple=on&redirect=on)

Good information there though some is old.

---

### Post by markus51 on 2018-05-18
If i try with sudo, it doesn't work.
I followed the Brother guide, nothing has changed.
With Ubuntu 16.04 simple scan works well with normal user.

It could be a bug: [https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/1728012](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/1728012)

---

### Post by DAB4970 on 2018-11-22
Do you have libsane-extras installed?  That worked to get my MFC-J615W to be detected under 18.04.

---

### Post by rwigle on 2018-11-23
It is disturbing that sane-find-scanner does not find the scanner. I solved a problem with my Brother DCP7065DN by adding the line:

brother4

to the end of /etc/sane.d/dll.conf but sane-find-scanner could see my scanner. I have attached my whole debug routine FYI. 

in bocca al lupo!

---

