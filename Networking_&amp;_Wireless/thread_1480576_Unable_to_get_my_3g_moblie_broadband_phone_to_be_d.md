---
title: "Unable to get my 3g moblie broadband phone to be detected by NetworkManager"
date: 2010-05-11
forum: Networking &amp; Wireless
---

### Post by Asheguy79 on 2010-05-11
I am having trouble getting NetworkManager to detect my Huawei-Vodafone dongle and I can't figure out why.  I went and checked on NetworkManagers website and I should be good to gobut no such luck.  Please look at the following:

manpep@manpep-desktop ~ $  
manpep@manpep-desktop ~ $ dmesg | grep -e "modem" -e "tty" 
[    0.000000] console [tty0] enabled 
[   47.951906] USB Serial support registered for GSM modem (1-port) 
[   47.951958] option 3-2:1.0: GSM modem (1-port) converter detected 
[   47.952990] usb 3-2: GSM modem (1-port) converter now attached to  ttyUSB0 
[   47.954710] option 3-2:1.1: GSM modem (1-port) converter detected 
[   47.954897] usb 3-2: GSM modem (1-port) converter now attached to  ttyUSB1 
[   47.954923] option 3-2:1.2: GSM modem (1-port) converter detected 
[   47.955151] usb 3-2: GSM modem (1-port) converter now attached to  ttyUSB2 
[   47.955414] option: v0.7.2:USB Driver for GSM modems 
manpep@manpep-desktop ~ $  
manpep@manpep-desktop ~ $  
manpep@manpep-desktop ~ $ lsusb 
Bus 007 Device 003: ID 0b38:0003   
Bus 007 Device 002: ID 058f:9254 Alcor Micro Corp. Hub 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 003: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB  Modem 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
manpep@manpep-desktop ~ $

Although "lsusb" see it (as usually) as Huawei model E620, in fact it's a  much more recent one. It's the K3520, from last year.  Any help or point in the right direction would be greatly appreciated 

Thanks,

-N

---

### Post by alexfish on 2010-05-11
hi

according to the messages the modem is ready to use and the driver is ready

 USB Serial support registered for GSM modem (1-port)
 option 3-2:1.0: GSM modem (1-port) converter detected
 usb 3-2: GSM modem (1-port) converter now attached to [COLOR=Blue]ttyUSB0[/COLOR]
 option 3-2:1.1: GSM modem (1-port) converter detected
 usb 3-2: GSM modem (1-port) converter now attached to [COLOR=Blue]ttyUSB1[/COLOR]
 option 3-2:1.2: GSM modem (1-port) converter detected
usb 3-2: GSM modem (1-port) converter now attached to [COLOR=Blue]ttyUSB2[/COLOR]
[COLOR=Blue] option: v0.7.2:USB Driver for GSM modems[/COLOR]

try to make the connection with Network Manager

if you don't see the make new connection select the VPN connections/configure VPN select " mobile broadband " add new

does  the modem shown up in the wizard , if so try to configure the modem

any luck

---

