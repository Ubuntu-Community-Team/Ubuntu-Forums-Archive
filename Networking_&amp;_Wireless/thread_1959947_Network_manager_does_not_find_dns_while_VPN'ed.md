---
title: "Network manager does not find dns while VPN'ed"
date: 2012-04-16
forum: Networking &amp; Wireless
---

### Post by Beware_Of_Pickles on 2012-04-16
Hello,

I am running Ubuntu 11.10 and installed network-manager-gnome with all available addons from the software center. I imported a pcf file for the VPN. When selecting the VPN at work or home, it shows that VPN is connected.
While I am at home I am able to connect to the machines on the other names. When i'm at work, I am not. I think it's because the client is not finding the DNS server. Is there a reason for that? When I ran the network manager in Fedora 16 it was able to find the DNS at my job and home.

Thanks.

---

### Post by sanderj on 2012-04-16
First things first: is your DNS really not available? Test with "host www.google.com" in all different situations.

---

### Post by Beware_Of_Pickles on 2012-04-16
> **sanderj said:**
> First things first: is your DNS really not available? Test with "host www.google.com" in all different situations.

Let me rephrase that. I can get to any outside world domain. I just can't access the virtual machines. I have not tried by using only the IP.

---

