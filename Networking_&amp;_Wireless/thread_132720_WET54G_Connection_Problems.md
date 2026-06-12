---
title: "WET54G Connection Problems"
date: 2006-02-18
forum: Networking &amp; Wireless
---

### Post by Piney Woods on 2006-02-18
I have a **WET54G linksys wireless bridge** that refuses to work in linux.  I have Ubuntu 5.10.  I did have it working and was able to access the internet before I swapped out my router (WRT546) with a newer WRT54GX.  Since then, I have not been able to get Ubuntu online.  I then tried it again with the old router and no dice.

In the networking configuration, I have eth0 set with DHCP and active.  I would appreciate any ideas, suggestions, etc....to get Ubuntu back online with the bridge.

Thanks,
PW

---

### Post by whatever123 on 2006-10-29
Did you finally get it working?  I have a similar problem....

---

### Post by bcymet on 2006-11-13
Hi, 

I also had the same problem. I was able to fix it by downloading the firmware upgrade from the linksys website. I think the firmware upgrade is from June 06 so it is fairly new. 

You will need a windows box to preform the upgrade. Or at least a box that can communicate with the bridge. After doing the firmware upgrade you will have to reset up the bridge by connecting it to your router. I also have my bridge set up to use DHCP and I am running Ubuntu 6.06. 

Hope this helps. If you have any questions please feel free to email me at 
bram.cymet AT gmail DOT com.

bcymet

---

### Post by jesterfred on 2008-02-25
I have a WET54G working - almost.

My Setup is:

Laptop - ETHERNET - WET54G - WIRELESS - WRT300N - LAN

The WET54G has a static IP address of 192.168.2.226 and my laptop assigned 192.168.2.227.  The WRT300N is in bridging mode - bridging between the wireless and the LAN.  My LAN is 192.168.2.0/24

The reason I have the laptop setup as static is that the WET54G seems not to pass DHCP requests/responses onto the LAN where the DHCP server sits.

Does anyone know how to solve this?

---

