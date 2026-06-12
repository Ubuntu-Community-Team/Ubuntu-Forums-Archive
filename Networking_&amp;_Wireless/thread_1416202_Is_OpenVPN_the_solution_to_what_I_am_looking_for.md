---
title: "Is OpenVPN the solution to what I am looking for?"
date: 2010-02-25
forum: Networking &amp; Wireless
---

### Post by harisund on 2010-02-25
ok so here's the situation - 

I have a public IP address from my ISP, let's say w.x.y.z. At this address, I have a TrendNet Wireless Router which acts as the gateway to my machines at home. I have two Linux desktops (One really very old, one just old). And one Windows 7 desktop. Here's the situation as far as IPs are concerned - 

The router has w.x.y.z on its public interface
The router has 192.168.5.5 on its private interface
The desktops acquire their IP through DHCP from the router, and have IPs in the 192.168.5.100-192.168.5.200 subnet with 255.255.255.0 netmasks. 

Finally, at work I have a Ubuntu workstation. 
-----------------
Question - 
Is there a way I can make the Ubuntu workstation a part of the home 192.168.5.0/24 network? Isn't this what VPN technically does? I want my workstation at work to be able to say "ssh 192.168.5.<something>" and be able to access my desktop, instead of doing all kinds of port forwarding on my router

-------------------------------------------------------------------------

(If this is not possible using my TrendNet wireless router as the gateway, will it be possible if I let my slower laptop be the gateway? In other words, I will make one of the desktops the router .. eth0 will now have w.x.y.z and eth1 will have 192.168.5.5, masquerading, dnsmasq etc .. will that help?)

---

### Post by kwacka on 2010-03-02
You will need a static IP address for your home connections, an alternative is a service such as [http://www.dyndns.com/]("http://www.dyndns.com/") (there are others) that spoof a static IP from a dynamic IP address. See [https://help.ubuntu.com/community/DynamicDNS]("https://help.ubuntu.com/community/DynamicDNS").

There are several methods for communicating between your home & work boxes - my preference is FreeNX, see [https://help.ubuntu.com/community/FreeNX]("https://help.ubuntu.com/community/FreeNX")

---

### Post by harisund on 2010-03-02
> **kwacka said:**
> You will need a static IP address for your home connections, an alternative is a service such as [http://www.dyndns.com/]("http://www.dyndns.com/") (there are others) that spoof a static IP from a dynamic IP address. See [https://help.ubuntu.com/community/DynamicDNS]("https://help.ubuntu.com/community/DynamicDNS").

There are several methods for communicating between your home & work boxes - my preference is FreeNX, see [https://help.ubuntu.com/community/FreeNX]("https://help.ubuntu.com/community/FreeNX")

Thanks for your reply, but I don't quite think you quite got my point :)

---

