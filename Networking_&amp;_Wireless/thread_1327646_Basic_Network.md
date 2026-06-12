---
title: "Basic Network"
date: 2009-11-15
forum: Networking &amp; Wireless
---

### Post by riversr54 on 2009-11-15
I'm sure this sort of question has been answered before but I can't seem to find the answers to my problem. First of all, I am a absolute newbie to Ubuntu and to Linux. I've installed Ubuntu Server on Sun Virtual Box on my laptop. My goal is to learn to manage a Linux server, particularly a Samba server. I've gone through the steps to configure Samba(at lease I think so). My problem is on the network side. Right out of the box Ubuntu was configured to use DHCP. It gets the following address: 10.0.2.15 I have no idea where that address is coming from. I currently use ICS on Windows and it provides ip addresses in the 192.168.0.x range. The Ubuntu server did get the correct DNS server address from ICS, so it appears that it is communicating with my DHCP service. At this point I can ping the laptop(Virtual Box Host) and even [www.google.com]("http://www.google.com") and everything is fine except that I can't ping the Ubuntu server from the laptop. I figured that was a firewall issue but have not found a problem with that. I tried manually configuring the eth0 interface with this info:
address: 192.168.0.201
netmask: 255.255.255.0
network: 192.168.0.0
broadcast: 192.168.0.255
gateway: 192.168.0.1
 
Laptop(VirtualBox host) is 192.168.0.200
 
After I configure it manually, I can't ping anything. I thought this would make it better but it did not. I set eth0 back to DHCP mode and the ping from Ubuntu to the laptop works again but not the other direction.
 
What am I doing wrong? I'm sure it's a basic network config problem, but I'm stuck!
 
Thanks,
 
riversr

---

### Post by riversr54 on 2009-11-15
Turns out my problem was with Virtual Box not with Ubuntu. I still don't understand where the DHCP address was coming from(maybe Virtual Box). Anyway...I now have it working. Now I can go and learn more about Samba Shares.
 
thxs

---

### Post by DGortze380 on 2009-11-15
> **riversr54 said:**
> Turns out my problem was with Virtual Box not with Ubuntu. I still don't understand where the DHCP address was coming from(maybe Virtual Box). Anyway...I now have it working. Now I can go and learn more about Samba Shares.
 
thxs

You're getting a DHCP Address from your Virtualization Software. It will NAT all traffic out to your subnet.

You want Bridged Networking if you want to access the VM as if it were a physical machine on the LAN.

---

