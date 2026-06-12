---
title: "more help with connecting telstra usb modem please"
date: 2009-08-22
forum: Networking &amp; Wireless
---

### Post by reddingo90 on 2009-08-22
Hi all, I hope someone can help me connect my telstra MF636BP USB stick .I have got my Toshiba Satellite Pro L300 laptop with 2.2 ghz 1gb of ram and a 160 hdd to see my modem but still can’t get it to connect. I also have tried to change my configuration in wvdial.conf  following others that I’ve read in forums but as you can see in this result using ttyUSB3 and using tty3 gives me different results and my lsusb with the dongle unplugged then plugged in _does_ show that it sees my modem but I just can’t get it to connect in Linux. I’m having to do all this in windows as it just connects automatically. Adrian
  



adrian@adrian-laptop:~$ sudo wvdial
  
  --> WvDial: Internet dialer version 1.60
  
  --> Cannot open /dev/ttyUSB3: No such file or directory
  
  --> Cannot open /dev/ttyUSB3: No such file or directory
  
  --> Cannot open /dev/ttyUSB3: No such file or directory
  
  adrian@adrian-laptop:~$ 



  
   This is what shows up after I change to tty3


  adrian@adrian-laptop:~$ sudo wvdial
  
  --> WvDial: Internet dialer version 1.60
  
  --> Cannot get information for serial port.
  
  --> Initializing modem.
  
  --> Sending: ATZ


My lsusb results


    adrian@adrian-laptop:~$ lsusb
    Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
    Bus 001 Device 002: ID 04f2:b070 Chicony Electronics Co., Ltd 
    Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    adrian@adrian-laptop:~$ lsusb
    Bus 002 Device 002: ID _19d2:0031  _
    Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
    Bus 001 Device 002: ID 04f2:b070 Chicony Electronics Co., Ltd 
    Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    adrian@adrian-laptop:~$

---

