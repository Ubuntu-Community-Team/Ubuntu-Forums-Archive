---
title: "ZTE MF 110 mobile internet"
date: 2010-08-03
forum: Networking &amp; Wireless
---

### Post by dancsa on 2010-08-03
hello.
Sorry for bother you again.
Today i bought an ZTE Mf 110 mobile internet stick   (provider djuice/telenor  Hungary)
I have Ubuntu 10.4 I can't connect with the gnome's utility, it starts to connect, but says: disconnected...  The APN, username, pass isn't wrong probably, because if i put the SIM in my cellphone, and i connect my it with USB cable (nokia 3110c) i can connect.

Syslog:
```
Aug  3 21:51:08 dancsa-laptop NetworkManager: <info>  Activation (ttyUSB1) starting connection 'Pannon USB-net'
Aug  3 21:51:08 dancsa-laptop NetworkManager: <info>  (ttyUSB1): device state change: 3 -> 4 (reason 0)
Aug  3 21:51:08 dancsa-laptop NetworkManager: <info>  Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) scheduled...
Aug  3 21:51:08 dancsa-laptop NetworkManager: <info>  Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) started...
Aug  3 21:51:08 dancsa-laptop NetworkManager: <info>  Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) complete.
Aug  3 21:51:08 dancsa-laptop nmbd[2019]: [2010/08/03 21:51:08,  0] libsmb/nmblib.c:834(send_udp)
Aug  3 21:51:08 dancsa-laptop nmbd[2019]:   Packet send failed to 192.168.2.255(138) ERRNO=Invalid argument
Aug  3 21:51:11 dancsa-laptop NetworkManager: <WARN>  stage1_prepare_done(): GSM modem connection failed: (32) Sending command failed: 'Resource temporarily unavailable'
Aug  3 21:51:11 dancsa-laptop NetworkManager: <info>  (ttyUSB1): device state change: 4 -> 9 (reason 1)
Aug  3 21:51:11 dancsa-laptop NetworkManager: <info>  Marking connection 'Pannon USB-net' invalid.
Aug  3 21:51:11 dancsa-laptop NetworkManager: <info>  Activation (ttyUSB1) failed.
Aug  3 21:51:11 dancsa-laptop NetworkManager: <info>  (ttyUSB1): device state change: 9 -> 3 (reason 0)
Aug  3 21:51:11 dancsa-laptop NetworkManager: <info>  (ttyUSB1): deactivating device (reason: 0).
```

I googled a lot about this modem, but, but neither gnome-ppp nor wvdial won't work.

---

### Post by alexfish on 2010-08-03
try connecting the device after booting the computer then try the connection

if it fails 

can you post the results of these codes from the terminal

Code:
ls -al /dev/serial/by-id/usb*

Code:
dmesg | grep -e "modem" -e "tty"

---

### Post by dancsa on 2010-08-06
Thanks, but i managed to get it to work ^^
I removed the packages: ozerocdoff, usbmodeswitch, and now it works (and if not, i do "rmmod usb_storage" and "modeprobe usbserial vendor=0x19d2 product=0x0001"
the only disadvantage is that i needed to remove the vodafone mobile connect (i have a huawei modem with pre-paid vodafone, but it was expensive)
Now i can use the gnome's network stuff to connect with both Huawei-vodafone and ZTE-Telenor.

Thanks again

---

### Post by alexfish on 2010-08-06
hi

not sure loading the usbserial drivers is the correct way to go

can you plug the device in after boot

and post the results of these codes from the terminal

Code:
lsusb

Code:

dmesg | grep -e "modem" -e "tty"

---

