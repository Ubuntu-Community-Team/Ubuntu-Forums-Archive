---
title: "Creating Udev Rule file for Modem"
date: 2013-01-03
forum: Networking &amp; Wireless
---

### Post by ketan985 on 2013-01-03
I have a modem with 16 ports using for sending SMS.
  When it's connected to my Linux machine, I get 16 ports from ttyUSB0 to ttyUSB15. Currently if I remove this modem and attached another it,I get it 16 ports from ttyUSB0 to ttyUSB15.
  How can I reserve first 16 ports for specific vendor with creating  udev file, so when I remove this modem it and insert another one, it is  assigned from ttyUSB16 onwards?
  
  My udev rule file Contents are as follows, which is working but port number  changes everytime I replug

Name=="Future Technology Devices International,Ltd",SUBSYSTEMS=="usb", ATTRS{idProduct}=="6011", ATTRS{idVendor}=="0403", SYMLINK="Ketan%b", KERNEL=="ttyUSB[0-15]*", MODE="0666", SYMLINK+="ttyUSB1",

Output

ls -l /dev/K* 
lrwxrwxrwx 1 root root 7 2013-01-08 15:09 /dev/Ketan-8.1 -> ttyUSB1
lrwxrwxrwx 1 root root 7 2013-01-08 15:09 /dev/Ketan-8.2 -> ttyUSB5 
lrwxrwxrwx 1 root root 8 2013-01-08 15:09 /dev/Ketan-8.3 -> ttyUSB11
lrwxrwxrwx 1 root root 8 2013-01-08 15:09 /dev/Ketan-8.4 -> ttyUSB12


Here ports are 16 but they are divided in Group of four. ttyUSB 1,5,11,12 Values are changing every time I Plug modem.
How I assign fix numbers to that ports ??

---

### Post by vasiliscnisrok on 2013-01-03
give me
```
lsusb
```

---

### Post by ketan985 on 2013-01-03
Here it is

>  root@AMPM:~# lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 0403:6011 Future Technology Devices International, Ltd 
Bus 001 Device 006: ID 0403:6011 Future Technology Devices International, Ltd 
Bus 001 Device 005: ID 0403:6011 Future Technology Devices International, Ltd 
Bus 001 Device 004: ID 0403:6011 Future Technology Devices International, Ltd 
Bus 001 Device 003: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 002: ID 0781:5567 SanDisk Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@AMPM:~# 




---

### Post by vasiliscnisrok on 2013-01-04
1) change KERNEL - remove *

```
SUBSYSTEMS=="usb", KERNEL=="ttyUSB[0-15]", ATTRS{idVendor}=="0403", ATTRS{product}=="6011", NAME=="AMPM" , SYMLINK=="AMPM", GROUP="tty", MODE="0660"
```

2) try
```
udevadm monitor --kernel --udev /dev/ttyUSB0
```

---

### Post by ketan985 on 2013-01-04
When I execute that command It does processing but it returns nothing showing just cursor,

kk@kk# udevadm monitor --kernel --udev /dev/ttyUSB*
monitor will print the received events for:
UDEV - the event which udev sends out after rule processing
KERNEL - the kernel uevent

---

