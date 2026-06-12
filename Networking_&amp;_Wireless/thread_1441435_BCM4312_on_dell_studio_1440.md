---
title: "BCM4312 on dell studio 1440"
date: 2010-03-28
forum: Networking &amp; Wireless
---

### Post by thegmoo on 2010-03-28
Howdy: 
I just got a new dell studio 1440 and installed 9.10 x64. I installed the driver with the hardware drivers tool from System => Administration => Hardware Drivers, selected to install the "Broadcom STA wireless driver". After a reboot wireless networking looks like its working but no wireless networks are listed. I should be seeing about a dozen as I live in a city. 

Here is what the system reports when I run lshw -C network: 
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0d:00.0
       logical name: eth1
       version: 01
       serial: 70:1a:04:de:b0:62
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:21 memory:f0300000-f0303fff

PLZ HELP!

---

### Post by 2hot6ft2 on 2010-03-28
[The Definitive 9.10 Broadcom Solution Guide]("http://ubuntuforums.org/showthread.php?t=1368699")

---

### Post by thegmoo on 2010-03-29
> **2hot6ft2 said:**
> [The Definitive 9.10 Broadcom Solution Guide]("http://ubuntuforums.org/showthread.php?t=1368699")

 Thanks for the reply. I can connect over a wired connection. I tried a fresh reinstall, updates/reboots, and then used the jockey interface to apply the driver. After a reboot both with and without the wired cable plugged in I cannot connect. I also tried to toggle the wireless on/off with the alt key but still no connection.  I did find some strange behavior on my own that I have not seen anywhere else. I can actually select to add a hidden network, supply my WPA password and it appears to connect to the access point. If I run ifconfig I receive a 10.x.x.x address when I should receive something in 192.168.1.100+. Even with this 10 address I cannot access the internet and I do not see any wireless networks listed in the manager.  Did that make sense? I hope so :) I am more than happy to run some commands and post the output if anyone has some ideas.  Thanks, TheGmoo

---

### Post by benprew on 2010-03-31
Hey,

I am having a similar problem.  I have been running 9.10 for a while without any problems, but I think the most recent kernel updates that I made a few days ago are not working with the new broadcom proprietary driver that was released in early February.

It appears that the driver is working correctly (according to dmesg) and that the wireless card is working.  ```
lsmod |grep wl
``` shows the wl driver installed, but I am unable to see any wireless networks and when I run ```
sudo iwlist scan
``` I get:

```
eth1      Failed to read scan data : Invalid argument 
```
I have even gone as far as download the proprietary driver from: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) and installing from source and I get the same error message from iwlist.

---

### Post by bkratz on 2010-03-31
> **benprew said:**
> Hey,

I am having a similar problem.  I have been running 9.10 for a while without any problems, but I think the most recent kernel updates that I made a few days ago are not working with the new broadcom proprietary driver that was released in early February.

It appears that the driver is working correctly (according to dmesg) and that the wireless card is working.  ```
lsmod |grep wl
``` shows the wl driver installed, but I am unable to see any wireless networks and when I run ```
sudo iwlist scan
``` I get:

```
eth1      Failed to read scan data : Invalid argument 
```
I have even gone as far as download the proprietary driver from: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) and installing from source and I get the same error message from iwlist.

You might look at the output of 

```
rfkill list
```

and see if some blocking shows up.

---

### Post by benprew on 2010-03-31
Hey,  Doesn't look like that's the problem...

benprew@studio:~/Downloads/foo$ rfkill list
```
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

---

### Post by 98cwitr on 2010-03-31
sudo lspci | grep Broadcom

if present:

```
sudo apt-get install ndiswrapper-common ndisgtk cabextract
```

download driver from Dell website

```
cabextract *driver.exe*
```

Administration->Windows Wireless Drivers (or something to that effect), find extracted .inf and click install.

Should be golden after a reboot.

---

### Post by wojox on 2010-03-31
Works fine on my end with Lucid:

```

[wojox@wojox-laptop ~]$ lspci | grep -i net
04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)

```

```
sudo apt-get install bcmwl-kernel-source
```

Reboot, Disconnect Ethernet Cable, and  click Network Manager Applet to connect to network.

---

### Post by bkratz on 2010-03-31
> **benprew said:**
> Hey,  Doesn't look like that's the problem...

benprew@studio:~/Downloads/foo$ rfkill list
```
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

If this is a Dell laptop there might be one more thing to consider--
As posted by Chili555 earlier;

try

```
sudo rmmod -f dell-laptop
```

If this helps we will need to make it permanent.

---

### Post by benprew on 2010-03-31
> **98cwitr said:**
> sudo lspci | grep Broadcom

if present:

```
sudo apt-get install ndiswrapper-common ndisgtk cabextract
```

download driver from Dell website

```
cabextract *driver.exe*
```

Administration->Windows Wireless Drivers (or something to that effect), find extracted .inf and click install.

Should be golden after a reboot.

I thought about this, but for the Studio 1440, the only driver they have for the wireless is for Windows Vista, so that seemed like a non-starter.  Is there somewhere else I should be looking?

Here's the link I was on.

[http://support.dell.com/support/downloads/driverslist.aspx?c=us&cs=19&l=en&s=dhs&ServiceTag=JQ4SHJ1&SystemID=studio1440&os=WLH&osl=en&catid=&impid=](http://support.dell.com/support/downloads/driverslist.aspx?c=us&cs=19&l=en&s=dhs&ServiceTag=JQ4SHJ1&SystemID=studio1440&os=WLH&osl=en&catid=&impid=)

---

### Post by benprew on 2010-03-31
> **bkratz said:**
> If this is a Dell laptop there might be one more thing to consider--
As posted by Chili555 earlier;

try

```
sudo rmmod -f dell-laptop
```

If this helps we will need to make it permanent.

Here's my wireless card, with device-id, is the 4315, which b43 only works if I'm using kernel 2.6.32, but ubuntu 9.10 is using 2.6.31-20

```
benprew@studio:~/Downloads/foo$ lspci -nn |grep Broad
11:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

```

Also, removing the dell_laptop module didn't seem to fix it either:

```

benprew@studio:~/Downloads/foo$ sudo rmmod -f dell_laptop
benprew@studio:~/Downloads/foo$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Failed to read scan data : Invalid argument

benprew@studio:~/Downloads/foo$ lsmod |grep dell
dell_wmi                2564  0 

```

---

### Post by benprew on 2010-03-31
> 

Also, removing the dell_laptop module didn't seem to fix it either:

```

benprew@studio:~/Downloads/foo$ sudo rmmod -f dell_laptop
benprew@studio:~/Downloads/foo$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Failed to read scan data : Invalid argument

benprew@studio:~/Downloads/foo$ lsmod |grep dell
dell_wmi                2564  0 

```

Forgot to mention, it looked like the module was dell_laptop, not dell-laptop:

```

benprew@studio:~/Downloads/foo$ sudo lsmod |grep dell
dell_wmi                2564  0 
dell_laptop             8128  0 
dcdbas                  7292  1 dell_laptop

```

---

### Post by bkratz on 2010-03-31
Sorry that didn't help, and thanks for the additional info.

---

### Post by benprew on 2010-03-31
> **bkratz said:**
> Sorry that didn't help, and thanks for the additional info.

No problem, if I can find a solution, I'll make sure to update this thread.

Thanks and if you think of anything else, don't hesitate to ask.

---

