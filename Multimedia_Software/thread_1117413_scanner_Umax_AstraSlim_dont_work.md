---
title: "scanner Umax AstraSlim dont work"
date: 2009-04-05
forum: Multimedia Software
---

### Post by timmson on 2009-04-05
Hello!
My scanner don't work
```

timmson@timmson-pc:/etc/sane.d$ lsusb 
Bus 001 Device 002: ID 05e3:0715 Genesys Logic, Inc. USB 2.0 microSD Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 012: ID 05d8:4009 Ultima Electronics Corp. Umax Astraslim
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

```

timmson@timmson-pc:/etc/sane.d$ more /etc/udev/rules.d/60-libsane.rules
# UMAX AstraSlim SE
SYSFS{idVendor}=="05d8", SYSFS{idProduct}=="4009", SYMLINK+="usb/scanner", MODE="666"

```

/dev/usb/scanner appear after plug and libusb is installed, but ...

```

timmson@timmson-pc:/etc/sane.d$ sudo sane-find-scanner -v
This is sane-find-scanner from sane-backends 1.0.19

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.
...
searching for USB scanners:
checking /dev/usb/scanner... failed to open (Invalid argument)
...
checking /dev/usbscanner15... failed to open (Invalid argument)
libusb not available
  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.
  # SANE has been built without libusb support. This may be a reason
  # for not detecting USB scanners. Read README for more details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
done

```

Does anybody know?

---

### Post by desertdog on 2009-04-18
According to the man page, [http://www.sane-project.org/man/sane-artec_eplus48u.5.html](http://www.sane-project.org/man/sane-artec_eplus48u.5.html), you have to get a driver from the windows installation cd and install in /usr/share/sane/artec_eplus48u/Artec48.usb

---

### Post by timmson on 2009-04-18
Thx for the reply! i did it before, but it dont work((

---

