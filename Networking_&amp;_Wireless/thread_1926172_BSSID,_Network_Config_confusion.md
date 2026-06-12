---
title: "BSSID, Network Config confusion?"
date: 2012-02-15
forum: Networking &amp; Wireless
---

### Post by VanillaFrappes on 2012-02-15
Hello, I am extremely new to all this, and I am horrible at connecting my internet even on Windows. I went through multiple threads on here and linuxquestions, however I only understood bits and pieces. 

I know that the BSSID is practically the same thing as the MAC address, and that's the physical address. XX-XX-XX-XX-XX-XX. From what I read, you can ignore the MAC address and just fill out the BSSID, correct? 

Now, another part I am curious about... When I try to type in my BSSID/MAC address the "save" option cancels out, unclickable. Why is that? I am running Ubuntu 11.10. 

Lastly, do I have to fill out the IPv4 address, or can I leave that blank? My network is Belkin and it's a WPA/WPA2. 

I hope I provided enough information, and thank you in advance for the help! Let me know if you need anymore information.

---

### Post by bkratz on 2012-02-16
> **VanillaFrappes said:**
> Hello, I am extremely new to all this, and I am horrible at connecting my internet even on Windows. I went through multiple threads on here and linuxquestions, however I only understood bits and pieces. 

I know that the BSSID is practically the same thing as the MAC address, and that's the physical address. XX-XX-XX-XX-XX-XX. From what I read, you can ignore the MAC address and just fill out the BSSID, correct? 

Now, another part I am curious about... When I try to type in my BSSID/MAC address the "save" option cancels out, unclickable. Why is that? I am running Ubuntu 11.10. 

Lastly, do I have to fill out the IPv4 address, or can I leave that blank? My network is Belkin and it's a WPA/WPA2. 

I hope I provided enough information, and thank you in advance for the help! Let me know if you need anymore information.

From wikipedia
"In an infrastructure BSS, the BSSID is the [MAC address]("http://en.wikipedia.org/wiki/MAC_address") of the [wireless access point]("http://en.wikipedia.org/wiki/Wireless_access_point") (WAP). In an IBSS, the BSSID is a locally administered MAC address generated from a 46-bit random number. "

Forget about the bssid and also mac address, (unless your router is using the mac for filtering) they are not required. Just leave them blank.
Also, don't worry about the ipv4 address either, just set it to automatic(dhcp). Set the essid (the network name) and the password if used.

---

