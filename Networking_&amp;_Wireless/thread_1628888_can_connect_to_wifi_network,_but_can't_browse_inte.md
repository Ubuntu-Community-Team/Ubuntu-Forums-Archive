---
title: "can connect to wifi network, but can't browse internet"
date: 2010-11-23
forum: Networking &amp; Wireless
---

### Post by typhoon71 on 2010-11-23
I am experiencing a strange issue with a fresh setup of ubuntu 10.10, fully updated on a LAN.  After the network manager has connected me to a open wifi network, I used to be able to browse the inet, download updates and packages (I still can do this if I boot windows, sadly).   

But now I do connect to the wifi network (or so the applet says), but can't browse at all, nor get packages. This thing happens just on the couple of wifi networks I'd need most, other ones seems fine.  To make things strange, there's the fact that I can ping IPs around, like google, ubuntu, just can't browse or use any other network thing.   

I've also the Wireless troubleshooting, gone till the IPv6 section and tried:  
sudo gedit /etc/modprobe.d/aliases (to set "alias net-pf-10 off")
 too bad the file doesn't exist     

I googled around and found another way to disable IPv6:   

sudo gedit /etc/sysctl.conf     
#disable IPv6  net.ipv6.conf.all.disable_ipv6 = 1 
net.ipv6.conf.default.disable_ipv6 = 1 
net.ipv6.conf.lo.disable_ipv6 = 1 

checking (cat /proc/sys/net/ipv6/conf/all/disable_ipv6) gives me the expected result, IPv6 is disabled.   

But the issue is still there...  then, can it be a DNS releted matter? but the IP for the DNS is right (access point one), so what?  Please, if someone can help, please do, I'm frustrated right now...

---

