---
title: "Problem on scanning"
date: 2007-08-10
forum: Multimedia &amp; Video
---

### Post by satimis on 2007-08-10
Hi folks,

Ubuntu 7.04 desktop
Scanner - Epson Perfection 3490 Photo


Evoked:
Application --> Graphics --> XSane Image Scanner```

Error
Failed to open device 'snapscan:libusb:001:002':invalid argument
```


Performed following steps;

$ sudo apt-get install sane-utils

# lsusb```

Bus 001 Device 003: ID 04b4:0001 Cypress Semiconductor Corp. Mouse
Bus 001 Device 002: ID 04b8:0122 Seiko Epson Corp. 
Bus 001 Device 001: ID 0000:0000  
```

# ls -ltr /proc/bus/usb/001```

total 0
crw-rw-r-- 1 root root    189, 0 2007-08-10 15:00 001
crw-rw-r-- 1 root root    189, 2 2007-08-10 15:00 003
crw-rw-r-- 1 root scanner 189, 1 2007-08-10 15:13 002

```

Shall I change owner as "root root'???

# find / -name libsane.db
# find / -name libsane.rules
Both without printout

# sane-find-scanner```

.....
found USB scanner (vendor=0x04b8 [EPSON], product=0x0122 [EPSON Scanner]) at libusb:001:002
.....

```

# scanimage -L```

device `snapscan:libusb:001:002' is a EPSON EPSON Scanner flatbed scanner

```

# scanimage -T```

[snapscan] Cannot open firmware file /usr/share/sane/snapscan/your-firmwarefile.bin.
[snapscan] Edit the firmware file entry in snapscan.conf.
scanimage: open of device snapscan:libusb:001:002 failed: Invalid argument

```


Pls advise how to fix the problem.  TIA


B.R.
satimis

---

### Post by seventyeights on 2007-08-11
Install and run scanbuttond to work around the bug.

More info in this thread:
[http://ubuntuforums.org/showthread.php?t=428382]("http://ubuntuforums.org/showthread.php?t=428382")

---

