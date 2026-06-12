---
title: "How to disable laptop RTL8187B wireless"
date: 2010-07-04
forum: Networking &amp; Wireless
---

### Post by installer on 2010-07-04
Hi, I'm running 10.04 LTS

I have loaded ndiswrapper and managed to get my D-Link usb dongle working (this is wireless N) but I need to disable my laptops built in rtl8187B wireless (they both connect at log on).

In Windows I just turn of the wireless switch but in Ubuntu this disables all wireless. I think I have to black list the rtl8178b driver, but I can't figure out how to do it.

---

### Post by flash63 on 2010-07-04
Hello,
i think you don't need Ndiswrapper. Name and ID of your D-Link Stick?
```
lsusb
```
Block the internal rtl8187
```
echo 'blacklist rtl8187' | sudo tee -a /etc/modprobe.d/blacklist.conf
```

---

### Post by installer on 2010-07-04
lsusb gives this

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c526 Logitech, Inc. MX Revolution Cordless Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0bda:8198 Realtek Semiconductor Corp. RTL8187B Wireless Adapter
Bus 002 Device 003: ID 07d1:3303 D-Link System 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



The D-Link dongle is a  DWA-131, it seemed not to work until I loaded ndiswrapper and xp drivers.

I have just run the echo comand and will now reboot and see if the internal wireless is now blocked.

Will post back, thanks.

---

### Post by installer on 2010-07-04
Update...

 blacklist comand worked, seems the problem was I entered RTL8187B and not rtl8187b into blacklist.conf.

As a side issue if the wireless switch is left off it does not now stop the usb dongle from working.

So unless anyone can confirm that I do not need ndiswrapper, problem solved.

---

### Post by flash63 on 2010-07-04
> 
The D-Link dongle is a DWA-131, it seemed not to work until I loaded ndiswrapper and xp drivers.
Ok
> ID 07d1:3303 D-Link System 
This is a Dlink DWA-131 or similar product with Realtek 8192su chipset. Driver Version 0006.20100625 available at ...

[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

---

### Post by installer on 2010-07-04
Thanks.

---

