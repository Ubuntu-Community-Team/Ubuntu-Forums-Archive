---
title: "Lost eth0 after installing a VPN"
date: 2011-06-15
forum: Networking &amp; Wireless
---

### Post by stevedude on 2011-06-15
Hello,

I wanted to try to install one of those public VPN services in order to try a software program. I setup a VPN for a service that is located in the UK. I am located in New York. 

I successfully installed the VPN that just required me to use their gateway address and they also supplied the username/password.

All I did was edit the connections from the Ubuntu Network Manager to add the VPN. After rebooting I no longer have my wired "eth0" connection listed and the Network Manager shows a red X.

I use a DSL service and my computer is directly connected to the router. I am using Ubuntu Natty 11.04. I read where you may have to edit the /etc/udev/rules.d/70-persistent-net.rules because it may cause an entry of eth1 instead of eth0. My file still shows eth0.

I have also deleted the contents of that file and rebooted, as suggested in other posts, and eth0 is in the file, but still does not show in my Network Manager.  

If I type in terminal: sudo ifconfig | grep eth, I get an output of: eth0 Link encap:Ethernet HWaddr [my mac address]

Going to Whois shows my IP address as that from my local ISP. Clicking on Network Manager > Connection Information, I receive a window that states : "No valid active connections found". Obviously, I am connected to the Internet.

Is there a way to restore my eth0 connection?

---

### Post by stevedude on 2011-06-16
OK, after some additional researching I came across this post: [http://ubuntuforums.org/showthread.php?t=1459907](http://ubuntuforums.org/showthread.php?t=1459907) , but instead of changing nm-system-settings.conf, which didn't exist on my system, I changed NetworkManager.conf.

You need to: sudo gedit /etc/NetworkManager/NetworkManager.conf

Change this file from 
```
[main] plugins=ifupdown,keyfile
  
[ifupdown] managed=false
```to this:
```
[main] plugins=ifupdown,keyfile
  
[ifupdown] managed=true
```...and reboot.

---

