---
title: "Wireless driver install for Linksys WMP600N on 8.04 LTS"
date: 2009-09-14
forum: Networking &amp; Wireless
---

### Post by wpsmithii on 2009-09-14
I now know that the Linksys WMP600N wireless pci card, is a Ralink RT2860 chipset. I've downloaded the linux driver from Ralinks website and extracted the archive to my desktop. I can't use ndiswrapper because the driver file on the cd and in "device manager" is a .sys file. What do I do now? Thanks in advance. Bill

---

### Post by Cuba71 on 2009-09-14
Unzip the file and save the drivers (rt2860.inf and rt2860.sys) to your Desktop. Then you can install them using ndisgtk. 
You can install ndisgtk from Synaptics and then use from System > Administration > Windows Wireless Drivers

---

### Post by wpsmithii on 2009-09-14
The drivers I got are linux not windows.

---

### Post by wpsmithii on 2009-09-22
OK, I've installed 9.04 and it sees the wireless connection, but it won't connect. Even with the wpa2 password. I'm trying to troubleshoot and the device is on and operating. It sees the two wirelss networks close to my house, mine and my neighbor's. When I check for device recognition I think it sees my wireless network as "ra0", not wlan0, when I type "sudo lshw -C network" I get "disabled" as part of the output. I'm at a loss, any help would be appreciated. Thanks Bill

---

### Post by grantjohnston on 2009-10-31
I'm getting the same problem. Can see the networks but cannot connect.



Anyone had a way to fix this?


Thanks



grant

---

### Post by wpsmithii on 2009-11-01
I hired a guy to come over and look at this problem. My router is a Dlink DIR615 and by default, I guess, it sets up "protected WIFI" when we disabled this and changed to WEP encryption it hooked up. I think the problem was with the PIN exchange for the protected WIFI not the encryption change. T upgraded to 9.10 and had no problems at all. Hope that helps Grant. Bill

---

