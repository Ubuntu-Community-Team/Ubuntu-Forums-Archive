---
title: "2 Nics - Pass traffic through 1 out the other"
date: 2011-04-13
forum: Networking &amp; Wireless
---

### Post by alienprdkt on 2011-04-13
What we are trying to do is setup a nTop bandwidth monitoring server. Place this server between router and firewall. I want all LAN traffic to go through the nTop server on one NIC, and out to the router on the other NIC. Any suggestions on how I can accomplish this.

Having very bad internet issues due to traffic, need to see whats happening.

Thanks in advance,

---

### Post by Jason0885 on 2011-04-13
I did something similar to this with IP Tables. This is what I done. 
The setup is using CENTOS 5.6, it is a basic pppoe conenction. The modem was in bridging mode. I bridged the pppoe interface and the eth1 interface. eth1 went to a wireless hotspot. 

In terminal type
1.) *sudo iptables -A INPUT -i lo -j ACCEPT*

2.) *sudo iptables -A OUTPUT -o lo -j ACCEPT*

3.) *sudo iptables --table nat --append POSTROUTING --out-interface **<interface>** -j MASQUERADE*

*<interface>* is your output interface. IE the one for your router. In my case eth1. Do not use the < and > signs if your if is eth1 just put eth1.

4.) *sudo service iptables save*

5.) S*udo nano /etc/sysctl.conf*
nano is the name of your text editor. I used nano for this machine.

6.) Add the following line to enable packet forwarding for IPv4:
*net.ipv4.conf.default.forwarding=1*

Save the file

sudo service network restart

When the computer reboots you may have to restart iptables by running
*sudo service iptables restart*

It should be similar, or even the same way. It should be at least in the right direction. I believe the term is called MASQUERADEING.

Good luck, I hope this helps.

---

