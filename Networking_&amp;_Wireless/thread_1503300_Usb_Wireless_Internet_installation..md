---
title: "Usb Wireless Internet installation."
date: 2010-06-06
forum: Networking &amp; Wireless
---

### Post by alexapoel on 2010-06-06
Hello guys,

I'm pretty new to the Ubuntu family and I need your help in order to gey my internet working. I am on a desktop pc, Intel Core 2 Quad CPU Q6600 @ 3.33ghz, with 8 gb ram, on a 64-bit operating system. In order to have internet I have a High Power 802.11 b/g/n WLAN USB Adapter and i can not install the drivers (newbie) i have the drivers on a cd and i have tried to follow the instructions but obviously i can not make it work. The usb adapter's name is JANUS and the webpage of the company is [www.hornettek.com](www.hornettek.com) 

What i'm asking is if anyone can write me down step by step instructions to get it work. THANKS IN ADVANCE.

---

### Post by chili555 on 2010-06-06
I think it would be fun but time consuming to compile a driver from source. However, there may be an easier way. Please open a terminal and do:```
sudo modprobe r8192s_usb
dmesg | grep 819
lsusb
```Please post the outcome and we'll know how to proceed.

---

### Post by alexapoel on 2010-06-06
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91544 r8192 d23144 u524288
[    0.000000] pcpu-alloc: s91544 r8192 d23144 u524288 alloc=1*2097152
[    0.763819] device-mapper: uevent: version 1.0.3
[    1.952991] ata5: SATA max UDMA/133 abar m8192@0xfdefe000 port 0xfdefe100 irq 16
[    1.952994] ata6: SATA max UDMA/133 abar m8192@0xfdefe000 port 0xfdefe180 irq 16
[   94.505659] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.
[   94.509454] Linux kernel driver for RTL8192 based WLAN cards
[   94.509494] usbcore: registered new interface driver rtl819xU


Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 046d:c525 Logitech, Inc. 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 041e:3040 Creative Technology, Ltd SoundBlaster Live! 24-bit External SB0490
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0603:00f2 Novatek Microelectronics Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0bda:8174 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by chili555 on 2010-06-06
> ID [COLOR="Red"]0bda[/COLOR]:[COLOR="Red"]8174[/COLOR] Realtek Semiconductor Corp. r8192s_usb is not correct for your device.

We could try to compile the driver that hornnetek provides. I downloaded it just now and was not successful. We could trick r8192s_usb into recognizing your device or we could try ndiswrapper.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

The driver CD you have has the needed .inf and other files. In case you have trouble extracting them, they are attached. Download the file to your desktop. Right-click it and select 'Extract Here.'

Now go to System > Administration > Windows Wireless Drivers and install the .inf file in the WinXP folder you extracted.

---

### Post by medad on 2010-06-06
Hi alexapoel,

I have a Belkin Model: F7D1101 v1 Basic Wireless USB adapter which is also uses the RealTek 8192SU driver.  The following website honestly helped work for me:  

[http://samiux.blogspot.com/2010/05/howto-realtek-8192su-usb-dongle.html](http://samiux.blogspot.com/2010/05/howto-realtek-8192su-usb-dongle.html)

This got me to where at least I could see wireless networks and connect to my router.

***Please read before you apply- there was a comment on the bottom of the page that might affect me in the future which might result with me having to re-compile the driver, but currently I haven't had an issue with connecting to my router under b/g.  

Good Luck,

Medad

---

### Post by alexapoel on 2010-06-07
> **chili555 said:**
> r8192s_usb is not correct for your device.

We could try to compile the driver that hornnetek provides. I downloaded it just now and was not successful. We could trick r8192s_usb into recognizing your device or we could try ndiswrapper.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

[B]The driver CD you have has the needed .inf and other files. In case you have trouble extracting them, they are attached. Download the file to your desktop. Right-click it and select 'Extract Here.'

Now go to System > Administration > Windows Wireless Drivers and install the .inf file in the WinXP folder you extracted.[/B]


how am i suppose to do the second part exactly? How to install the .inffile in the winxp folder?

---

### Post by chili555 on 2010-06-07
Go to System > Administration > Windows Wireless Drivers and click 'Install New Driver.' Select 'Location' and browse to Desktop > WinXP and select the .inf file. It should handle the rest for you.

Next, can you click the Network Manager icon, see networks and connect?

---

