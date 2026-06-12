---
title: "Can't connect to the internet after switching ISP's!"
date: 2012-01-09
forum: Networking &amp; Wireless
---

### Post by MollyWop on 2012-01-09
So recently, my dad switched over from ATT to a small internet company called CopperNet DSL. We bought a brand new Actiontec GT724WGR because our old ATT router didn't seem to be compatible with our new ISP. They told us that a new router would probably fix the problem. Nothing seems to work though, the DSL light will light up on the new router, but it just won't connect to the internet. No matter what I do! The weird thing is that an old D Link DSL modem will work with our desktop on both Operating Systems, but won't work with my PS3 or any other laptop in the house. 

I was told to connect to the internet via PPPoE by the coppernet customer support reps, but I've tried this in the Actiontec router config, and directly with my PS3/PC/Laptop and nothing will connect. Is there something wrong with the ISP that won't connect me to the internet? I've seriously tried everything from taking off the phone line filters from the wall. Someone please help me! I haven't had any internet in the house for weeks! 

My dad said that it's on CopperNets end. I got the internet light to come onto the router by selecting DHCP Static IP or something and it connects to the internet, but always gives me a DNS error..

---

### Post by prshah on 2012-01-10
> **MollyWop said:**
> My dad said that it's on CopperNets end. I got the internet light to come onto the router by selecting DHCP Static IP or something and it connects to the internet, but always gives me a DNS error..

I'd suggest that you wait for CopperNet support tech to come take a look. If that is not convenient/possible, then you can try the following:

On the same location as where you have chosen static ip, you will also find boxes for DNS servers. Get CopperNet's DNS server addresses from their tech support, and enter it here.

If you cannot get the DNS addresses from them, then you can try any ONE PAIR of the following free global DNSs:
a) OpenDNS: Primary: 208.67.222.222, Secondary: 208.67.220.220
b) Google Public DNS: Primary: 8.8.8.8 Secondary: 8.8.4.4

DNS is the service used to translate website names (Eg [www.google.com](www.google.com)) into their IP addresses.

Hope this helps.

EDIT: CopperNet's DNS settings SEEM to be:
DNS Settings

DNS Server Addresses: 
Preferred DNS Server	62.56.216.9
Alternate DNS Server 	62.56.217.15

You can use any ONE of the three pairs (OpenDNS, Google DNS OR CopperNet DNS) mentioned above.

---

