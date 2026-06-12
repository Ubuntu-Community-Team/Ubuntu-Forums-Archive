---
title: "VM Ubuntu 11.04 Cannot use Network"
date: 2011-10-06
forum: Networking &amp; Wireless
---

### Post by RIT_girl on 2011-10-06
Hello, 

I am trying to run a VM (configured in VMWare player) for ubuntu 11.04 on Windows 7. I have bridged the network connection, and on my device tools I can see it receiving packets, but it is not transmitting. 

I noticed my IP for the VM and my host PC are different. But it fails when I try to ping my host. I am using a wired connection. 

I'm really a beginner at this, but I'm sure its something to do with the proxy settings.

---

### Post by haqking on 2011-10-06
> **RIT_girl said:**
> Hello, 

I am trying to run a VM (configured in VMWare player) for ubuntu 11.04 on Windows 7. I have bridged the network connection, and on my device tools I can see it receiving packets, but it is not transmitting. 

I noticed my IP for the VM and my host PC are different. But it fails when I try to ping my host. I am using a wired connection. 

I'm really a beginner at this, but I'm sure its something to do with the proxy settings.

is the VM IP on the same subnet as the host and using the same gateway (your router typically) ? as for pinging are there any firewalls involved either side ?

---

### Post by RIT_girl on 2011-10-06
There is a corporate firewall on the windows 7 side. No way to disable it. 


Same subnet. Not sure on how to check the gateway in this version, I didn't see anything that seemed to correspond to it in the network tools.

---

### Post by haqking on 2011-10-06
> **RIT_girl said:**
> There is a corporate firewall on the windows 7 side. No way to disable it. 


Same subnet. Not sure on how to check the gateway in this version, I didn't see anything that seemed to correspond to it in the network tools.

I suspect the corporate firewall is not trusting the VM, depending on how that is set up, you have effectively placed a new machine on the network using bridged and so that machine (virtual or not) needs to be a trusted entity i suspect.

depending on the security of your LAN it probably doesnt allow rogue machines to be placed on the network.

However unless you mean it is a firewall installed on your Windows 7 Host  ?

is the bridged networking using the correct device on the host ?

as for not knowing the gateway, did you not add the IP to the bridged device then ? or is the bridge relying on DHCP from your LAN, which again brings us back to the security of the DHCP server possibly ?

However i may be over complicating all this, but i dont know your total setup or environment or IP range etc

---

### Post by RIT_girl on 2011-10-06
I'm thinking I'll have to configure it off the network (at home), unfortunately I don't have the bride connection capabilities because I'm using freeware. Stay tuned,I'll probably be back after 6 with more questions on it.

---

### Post by haqking on 2011-10-06
> **RIT_girl said:**
> I'm thinking I'll have to configure it off the network (at home), unfortunately I don't have the bride connection capabilities because I'm using freeware. Stay tuned,I'll probably be back after 6 with more questions on it.

ok no problem.

a tip, try using virtual box instead [www.virtualbox.org](www.virtualbox.org) it is free and fully functional and IMO better than anything else out there for the end user

---

