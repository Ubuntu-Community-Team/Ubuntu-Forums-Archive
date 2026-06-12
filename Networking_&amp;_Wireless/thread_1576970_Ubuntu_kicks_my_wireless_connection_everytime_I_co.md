---
title: "Ubuntu kicks my wireless connection everytime I connect"
date: 2010-09-18
forum: Networking &amp; Wireless
---

### Post by dnstth on 2010-09-18
Hello there,


I am pretty new to Linux, just installed 10.04 version. I really like it, but I have a serious problem with my wireless connection. Everytime I connect it kicks the wireless connection after a few seconds, and the biggest problem is that it also kicks the wireless connection for the other users, too.

Here are my wireless connection details:


sudo lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 02
       serial: 00:1c:bf:57:43:8f
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:30 memory:f8000000-f8000fff
  *-network

and...it is DISABLED because I turned it off :)

I went through several wireless problems in the forums, but I could not find any info on this.

Also we are using WPA/WPA2 encryption.

Thank you very much for your help,

D.

---

### Post by grahammechanical on 2010-09-18
I do not understand how a Operating System could stop a modem/router from working, especially if it was accessing the modem over a wireless connection. Are you sure the modem is connected to the mains power supply properly? What do the indicator lights on the modem reveal? Do other users cause this problem when you are not using your computer and they are? Or, does this only happen when you are using your computer? Could still be coincidence. Check the modem. Is it broadband? Do you have microfilters fitted on every telephone socket that has a device (phone, etc.) fitted?

regards.

---

### Post by dnstth on 2010-09-18
well, it is interesting for me, too. there are three of us connected to the wireless router, all through wireless connection. everything is working fine if all of us is connected from windows. at the moment I restart and boot to Ubuntu, it connects to the wirelss network. after a few seconds it says disconnected, and also my flatmates run out of their room madly that what's going on :) also, we do not have any phonejacks in the flat, so I have no idea what is causing the problem. this problem is only present when I boot to Ubuntu, that is why I am looking for the resolution here. 

we had similiar problems before, but it was caused by windows XP and a thrid-party software 'beating' for managing the wireless properties of the XP. we just uninstalled the third-party software and let the XP manage it, now the problem only comes up when I boot to Ubuntu. Unfortunately, it is very annoying to me as I can only use it through I wired connection. 

Is there any other software that can manage the wireless properties of Ubuntu?

maybe someone out there who had similar problem?

Thanks. D.

---

