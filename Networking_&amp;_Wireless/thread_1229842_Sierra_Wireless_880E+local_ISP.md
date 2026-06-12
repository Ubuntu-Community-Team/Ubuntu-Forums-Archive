---
title: "Sierra Wireless 880E+local ISP"
date: 2009-08-02
forum: Networking &amp; Wireless
---

### Post by cybrosh on 2009-08-02
Good day,

I have Ubuntu 9.04 on my lenovo/ibm x61 thinkpad.

Used to have a Merlin 870u which worked flawlessly with Network Manager. Switched ISP's(Mobile Phone providers-3G), and received a new 3G Express Card - Sierra Wireless 880E. 

After trying endlessly to get it to work with NM, researched a bit and found an open BUG. It can't workwith NM. Maybe in the next OS upgrade?

ANyhow, found several solutions...Driver upgrade, WVDIAL(3 different scripts), GSM_CHAT, KPPP/Gnone PPP(various settings). I can connect to the 3G network using all methods, receive ip through DHCP, DNS servers and a default gw, but I can't get DNS or the GW to work. I can ping them 'internally', but can't get out.

Using Windows, works perfect...same DNS servers, different GW. 

So...tried to modify the GW, succeeded in changing, but it did nothing. Tried different DNS servers...nothing. 

Furthermore, when trying to ping both GW's, I get "Time to live exceeded". ICMP issue.

Any thoughts?????

Cheers

---

### Post by GeorgeVita on 2009-08-02
Hi **cybrosh**, please try the following:

Boot without the modem, wait for the system to load, attach the modem, wait 10 seconds, open a terminal window and try:```
lsusb
``````
dmesg
```
Copy here the output of **lsusb** and the last 10-15 lines of **dmesg** that possibly have some info about the modem.

**>>> EDIT**: I found also an older possibly [similar case]("http://ubuntuforums.org/showthread.php?t=1217705") which solved into post#4 by ['trimming' HAL info]("http://docs.google.com/Doc?id=d9khzpw_0w4m774dd").

Regards,
George

---

### Post by cybrosh on 2009-08-03
Hi George,

Thanks for replying.

lsusb : 
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 003: ID 1199:6852 Sierra Wireless, Inc. AirCard 880E Device
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 04d9:1400 Holtek Semiconductor, Inc. 
Bus 001 Device 003: ID 17ef:1000 Lenovo 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a5c:2110 Broadcom Corp. Bluetooth Controller
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

dmesg:
[  399.954317] USB Mass Storage support registered.
[  399.984089] usb 7-3: USB disconnect, address 2
[  401.508081] usb 7-3: new full speed USB device using ohci_hcd and address 3
[  401.721247] usb 7-3: configuration #1 chosen from 1 choice
[  401.787353] usbcore: registered new interface driver usbserial
[  401.787382] USB Serial support registered for generic
[  401.787470] usbcore: registered new interface driver usbserial_generic
[  401.787474] usbserial: USB Serial Driver core
[  401.804902] USB Serial support registered for Sierra USB modem
[  401.804970] sierra 7-3:1.0: Sierra USB modem converter detected
[  401.807204] usb 7-3: Sierra USB modem converter now attached to ttyUSB0
[  401.807291] usb 7-3: Sierra USB modem converter now attached to ttyUSB1
[  401.807382] usb 7-3: Sierra USB modem converter now attached to ttyUSB2
[  401.807411] usbcore: registered new interface driver sierra
[  401.807416] sierra: v.1.3.2:USB Driver for Sierra Wireless USB modems



Regarding the driver - strange, thought I've upgraded it to 1.7.2

Sure not about the Hal solution since it's a USB modem, and this is an ExpressCard. But who knows?

Quite odd - we have the same gateway 10.64.64.64 under ubuntu when connecting through the 3G card.

---

### Post by GeorgeVita on 2009-08-03
Hi **cybrosh**,
your modem lists as **1199:6852** and if the link for 'trimming' the HAL info is correct you could simply try:
```
sudo gedit /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi
```

Search into this file for **1199** (Sierra Wireless vendorID). Some lines below you have to check that **6852** is included within **usb.product.id**

The 'trim' you can check is changing **usb.interface.number** and **serial.port** from default **0** to **2** or **4** (data extracted from [http://sierrawireless.custhelp.com/app/answers/detail/a_id/500](http://sierrawireless.custhelp.com/app/answers/detail/a_id/500)).

It is better to try the connection after a reboot.
Remember that a future upgrade could possibly return this file to original data.

General Notice: From 9.04 some methods regarding USB peripherals are changing. Using HAL is not a 'modern' method but till your peripheral will be included in the 'new style' you have to use it...!

Regards,
George

---

### Post by cybrosh on 2009-08-03
George - Do I change the usb.interface.number+serial port in VendorID or ProductID, or both?

---

### Post by GeorgeVita on 2009-08-03
I am not sure! From other examples these numbers are always the same. It will be hard to try all but ... just imagine the connection!

Hope to make it!
g

---

### Post by cybrosh on 2009-08-03
George, tried it on both, didn't work. Same issue - All connection methods work same as before. NM doesn't recognize the card.

---

