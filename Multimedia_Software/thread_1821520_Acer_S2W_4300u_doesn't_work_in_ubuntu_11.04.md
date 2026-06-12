---
title: "Acer S2W 4300u doesn't work in ubuntu 11.04"
date: 2011-08-09
forum: Multimedia Software
---

### Post by naelphin on 2011-08-09
I am trying to get my Acer S2W 4300u to work in Ubuntu 11.04 32bit.

It is linked as supported on this webpage [http://snapscan.sourceforge.net/](http://snapscan.sourceforge.net/)

But the instructions are very lacking. I found the firmware that is necessary and have put it in /usr/share/sane/snapscan/ but sane doesn't pick it up at all.

I have installed sane and xsane

Sane info
```
acer@ubuntu:~$ sane-find-scanner 

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04a5 [Color], product=0x20de [ FlatbedScanner 13]) at libusb:005:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
```

lsusb

```
acer@ubuntu:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 04a5:20de Acer Peripherals Inc. (now BenQ Corp.) S2W 4300U+
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0c45:7000 Microdia 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 064e:a103 Suyin Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by naelphin on 2011-08-09
This page supposedly is how someone managed to make it work in Ubuntu, but it doesn't work either

[http://pkorir.blogspot.com/2010/07/making-my-benq-acer-4300-scanner-to.html](http://pkorir.blogspot.com/2010/07/making-my-benq-acer-4300-scanner-to.html)

---

