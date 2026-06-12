---
title: "USR dial up modem NOT working on Ubuntu 9.10 (wubi)"
date: 2010-01-08
forum: Networking &amp; Wireless
---

### Post by Silvertones on 2010-01-08
I just can't seem to get this thing going. I've also tried Gnome-ppp. Press detect and it says "no modem installed"
I did install it in Windows as well to make sure the darn thing actually works. It did perfectly.


Your **US Robotics modem** attached at **/dev/ttyACM0**
>>> The **problem**t: **wvdial** for some reason [B]cannot use it

I had to edit the /etc/wvdial.conf file with gksudo gedit /etc/wvdial.conf

[/B]    john@ubuntu:~$ sudo wvdial
  [sudo] password for john: 
  --> WvDial: Internet dialer version 1.60
  --> Cannot get information for serial port.
  --> Initializing modem.
  --> Sending: ATZ
  --> Sending: ATQ0
  --> Re-Sending: ATZ
  --> Modem not responding.

I can see the data lights flashwhen sending. Gnome-ppp says "can't open modem"
  
  john@ubuntu:~$
   john@ubuntu:~$ lsusb
  
  Bus 001 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
  Bus 001 Device 002: ID 0baf:0303 U.S. Robotics 
  Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  
      john@ubuntu:~$ dmesg
  
  [  149.192070] usb 1-1: new full speed USB device using uhci_hcd and address 3
  [  149.360927] usb 1-1: configuration #1 chosen from 1 choice
  [  149.859257] cdc_acm 1-1:1.0: ttyACM0: USB ACM device
  [  149.862438] usbcore: registered new interface driver cdc_acm
  [  149.862453] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters

---

### Post by Silvertones on 2010-01-08
I had a thought. I didn't uninstall the builtin winmodem. Should I have? Could it be interfeering. USR says to first uninstall. Didn't affect Windows though.:redface:

---

### Post by Silvertones on 2010-01-09
IT IS SOLVED.
It took fore ever to find a confirmed bug in Ubuntu BUG#469881.

Uninstall moddemmanager & Gnome-ppp works like a charm.
I'm using it now.

[https://bugs.launchpad.net/ubuntu/+bug/469881](https://bugs.launchpad.net/ubuntu/+bug/469881)

---

### Post by Bartender on 2010-01-09
Jeez.  One more reason to avoid 9.10.  Ubuntu dial-up just keeps getting worse and worse with each release.

---

