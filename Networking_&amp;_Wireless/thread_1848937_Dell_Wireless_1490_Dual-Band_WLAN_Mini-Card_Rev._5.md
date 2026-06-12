---
title: "Dell Wireless 1490 Dual-Band WLAN Mini-Card Rev. 5.8 broadcom STA driver doesnt work"
date: 2011-09-23
forum: Networking &amp; Wireless
---

### Post by Paradox268 on 2011-09-23
My Dell Lattitude D830 wireless doesnt want to work.
Chipset is BCM4312/BCM2050

I have tryed to fix it but had no luck.

---

### Post by garvinrick4 on 2011-09-23
I believe you can open synaptics and install what I have marked and hit apply arrow. make sure
nothing else marked  and or installed take wired out and reboot.  Notice I put bcm in search window.
Here is link for command line and if have 10.04 installed use graphics in link. If need help hollar.
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by Paradox268 on 2011-09-23
it did something; now under the network connections, the wireless just disappeared and I can Access it at all

---

### Post by garvinrick4 on 2011-09-23
Supported models include: 
BCM4311, BCM4312, BCM4313, BCM4321, BCM4322, BCM43224, BCM43225, **BCM43227, **BCM43228 
 
**STA - Internet access**

 **Step 1.**  
Install the STA hybrid drivers/firmware from the [restricted repository]("https://help.ubuntu.com/community/Repositories/Ubuntu") using the **Software Centre** or the **Synaptic Package Manager** (Under the desktop menu **System > Administration > Synaptic Package Manager**) and search for the bcmwl-kernel-source package and install **or** in a **terminal** (under the desktop menu **Applications > Accessories > Terminal**) issue the following commands: 

~$ sudo apt-get update ~$ sudo apt-get install bcmwl-kernel-source**Step 2.** 
Under the desktop menu **System > Administration > Hardware/Additional Drivers**, the **STA** drivers can be activated for use. 
**Note:**  In [COLOR=Red]Ubuntu 11.04[/COLOR], if the driver fails to load, you may need to reinstall  the bcmwl-kernel-source package. This can be done from Synaptic ->  Mark for Reinstallation.  
**Note:** A computer restart may be required before using the wifi card.

---

### Post by Paradox268 on 2011-11-18
Thank you!!

---

