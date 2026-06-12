---
title: "Huawei E3231"
date: 2013-01-30
forum: Networking &amp; Wireless
---

### Post by hamstermoon on 2013-01-30
Having just lost my old mobile internet dongle I have just bought a new one.  It's a E3231 and Xubuntu isn't recognising it. 

I believe, having had dongle problems before, it might be fairly new (came out in August) and need a driver.

Suggestions please!

---

### Post by audiomick on 2013-01-30
make sure the package usb-modeswitch is installed. I believe it is default on standard Ubuntu, but check it is there. 

What the package does is switch the bit that gets switched when the installer is run on a Windows machine so that the device can be seen as a modem and not only as a storage medium.

---

### Post by hamstermoon on 2013-01-30
That is certainly installed. It seems to be seeing it as something odd:

[https://picasaweb.google.com/lh/photo/rRdoI9sdspyoohFWlGLSudMTjNZETYmyPJy0liipFm0?feat=directlink](https://picasaweb.google.com/lh/photo/rRdoI9sdspyoohFWlGLSudMTjNZETYmyPJy0liipFm0?feat=directlink)

---

### Post by sanderj on 2013-01-30
> **hamstermoon said:**
> Having just lost my old mobile internet dongle I have just bought a new one.  It's a E3231 and Xubuntu isn't recognising it. 

I believe, having had dongle problems before, it might be fairly new (came out in August) and need a driver.

Suggestions please!

What is the USB ID of the UMTS device? Check with "lsusb"
What does "dmesg" say when you click in the UMTS dongle?

---

### Post by audiomick on 2013-01-30
Hmm, can't make much sense out of that. 

It seems, though, that the device is being seen.

On standard Ubuntu, you can right click on the network icon, choose the option "edit connections", go to the tab "mobile broadband" and the option "add" to set up a 3G dongle. I assume there is something similar on Xubuntu. Have you tried that process?

---

### Post by hamstermoon on 2013-01-30
> **sanderj said:**
> What is the USB ID of the UMTS device? Check with "lsusb"
What does "dmesg" say when you click in the UMTS dongle?

You'll have to talk me through that step by step!

---

### Post by sanderj on 2013-01-30
> **hamstermoon said:**
> You'll have to talk me through that step by step!

Cool! ;-)

Plug in the UMTS dongle, open a terminal (you know what that is, right?), and type:

lsusb

Post the output here. Tip: with your mouse you can select the text, and then paste it here by pressing the middle mouse button.

(dmesg instruction after you do the lsusb stuff)

---

### Post by hamstermoon on 2013-01-30
Here is the lsusb paste

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 1d57:2400  
Bus 002 Device 003: ID 12d1:14db Huawei Technologies Co., Ltd. 

the dmesg was so huge I can't copy it.

You know the other weird thing? The dongle now seems to be working on its own. The computer seems to be seeing it as 'wired connection 2' (see the link to to the screen grab in an earlier post) and it's working fine.  I didn't have to even set up the connection, and there is nothing to tell me how strong the signal is as was with my old dongle (which is a bit inconvenient). Very odd!

---

### Post by sanderj on 2013-01-30
Good that it works.

FWIW: instruction for dmesg:

Unplug UMTS dongle
Open a terminal, and type "dmesg". Notice the time-counter of the last line. Press ENTER a few times.
Now plugin the dongle. Wait 30 seconds. Then type "dmesg" again, and copy everything from the last known line up to the end, and copy-paste it here.

---

### Post by hamstermoon on 2013-01-30
here you go:

[ 1906.428058] usb 2-2: new high-speed USB device number 6 using ehci_hcd
[ 1906.572919] scsi6 : usb-storage 2-2:1.0
[ 1907.594253] scsi 6:0:0:0: CD-ROM            Huawei   Mass Storage     2.31 PQ: 0 ANSI: 2
[ 1907.628828] sr0: scsi-1 drive
[ 1907.631711] sr 6:0:0:0: Attached scsi CD-ROM sr0
[ 1907.632881] sr 6:0:0:0: Attached scsi generic sg1 type 5
[ 1908.366573] usb 2-2: USB disconnect, device number 6
[ 1908.744064] usb 2-2: new high-speed USB device number 7 using ehci_hcd
[ 1908.892397] cdc_ether 2-2:1.0: eth1: register 'cdc_ether' at usb-0000:00:13.2-2, CDC Ethernet Device, 58:2c:80:13:92:63
[ 1920.088024] eth1: no IPv6 routers present

---

### Post by sanderj on 2013-01-30
> **hamstermoon said:**
> here you go:

[ 1906.428058] usb 2-2: new high-speed USB device number 6 using ehci_hcd
[ 1906.572919] scsi6 : usb-storage 2-2:1.0
[ 1907.594253] scsi 6:0:0:0: CD-ROM            Huawei   Mass Storage     2.31 PQ: 0 ANSI: 2
[ 1907.628828] sr0: scsi-1 drive
[ 1907.631711] sr 6:0:0:0: Attached scsi CD-ROM sr0
[ 1907.632881] sr 6:0:0:0: Attached scsi generic sg1 type 5
[ 1908.366573] usb 2-2: USB disconnect, device number 6
[ 1908.744064] usb 2-2: new high-speed USB device number 7 using ehci_hcd
[ 1908.892397] cdc_ether 2-2:1.0: eth1: register 'cdc_ether' at usb-0000:00:13.2-2, CDC Ethernet Device, 58:2c:80:13:92:63
[ 1920.088024] eth1: no IPv6 routers present

Fascinating: your UMTS dongle becomes an "eth" device (eth1)?

Next check: with the UMTS dongle inserted (and active?), do you see an "eth1" in the output of "ifconfig"? I guess so ...

---

### Post by oldgraf on 2013-01-30
From my memories there is builtin cdrom with drivers/software to compile/install

---

### Post by bmork on 2013-01-30
> **sanderj said:**
> Fascinating: your UMTS dongle becomes an "eth" device (eth1)?

Next check: with the UMTS dongle inserted (and active?), do you see an "eth1" in the output of "ifconfig"? I guess so ...

This is normal for these so called "HiLink" modems.  They are configured using a browser.  Enable DHCP on the interface and connect to it using a browser
[http://192.168.1.1/](http://192.168.1.1/)


Bjørn

---

### Post by hamstermoon on 2013-01-31
Wow you are right. Thanks!

---

### Post by hamstermoon on 2013-01-31
> **sanderj said:**
> Fascinating: your UMTS dongle becomes an "eth" device (eth1)?

Next check: with the UMTS dongle inserted (and active?), do you see an "eth1" in the output of "ifconfig"? I guess so ...

Here you go. 

eth0      Link encap:Ethernet  HWaddr 40:61:86:ba:68:b3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 58:2c:80:13:92:63  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::5a2c:80ff:fe13:9263/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3463 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3000 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2254803 (2.2 MB)  TX bytes:515000 (515.0 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:70 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8786 (8.7 KB)  TX bytes:8786 (8.7 KB)

BTW: bmork posting below seems to have cracked the problem. I am not apparently supposed to be looking for the interface via an indicator plugin but by looking using my browser. That tells me what I need to know (phew).

---

### Post by Cfossy2 on 2013-07-05
I have used part of the above methods, in as much as I connected the dongle, then entered the network address 192.168.1.1 then went through the sytem and other settings of the dongle, making sure that i saved each setting as I went along, then rebooted the device. then i added a new wireless  mobile broadband, but it seemed to connect using ethernet or wired connection, without any problems, so far. i am using ubuntu 12.04 LTS, so hopefully it will still be OK, after updating it. I was then able to connect to the internet, surf and collect emails. Hope this helps.

---

### Post by marbew on 2013-11-12
Hei did you solve your problem with the dongle?

---

