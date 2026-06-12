---
title: "VPN and dynamic IP"
date: 2012-12-26
forum: Networking &amp; Wireless
---

### Post by kakotako on 2012-12-26
I have 10.04 LTS - the Lucid Lynx. I just setup VPN PPTP with my DD-WRT router at home. The tunneling seems to work.

There is no provision in the Network Manager's VPN configuration to use a third party dynamic IP DNS service like dynDNS.com.

I can easily tell the WAN IP address of my router in the command line and modify the VPN configuration in Network Manager when the IP address changes, but I'm really setting this up for my mom and manual configuration is not an option.

I could write a script to figure out the IP address, and if changed update the Network Manager's VPN config file, but I can't find such file. I looked at the files in myuser/.gconf/system/networking/connections and although there are some files that mention VPN and that were created at the same time I setup my VPN connection, they are not what I am looking for.

Can someone point me to user editable VPN config files for Network Manager or a better way to integrate a service like dynDNS.com with the VPN client?

---

### Post by ahallubuntu on 2012-12-26
DD-WRT supports dynamic DNS services.  So, just sign up for one of those services and use the domain instead of the IP.  Let DD-WRT update the domain as the IP changes.  And when connecting to the VPN, use the domain not the IP.  

In other words, Network Manager or the VPN doesn't need to deal with a changing IP at all.  Let DD-WRT do it by managing the domain.

---

### Post by kakotako on 2012-12-26
> **ahallubuntu said:**
> And when connecting to the VPN, use the domain not the IP.

I tried that at first and it didn't connect for some reason. Then I tried it again after your advice and it worked. Thanks.

---

