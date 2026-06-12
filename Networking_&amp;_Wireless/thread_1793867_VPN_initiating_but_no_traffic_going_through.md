---
title: "VPN initiating but no traffic going through"
date: 2011-06-30
forum: Networking &amp; Wireless
---

### Post by semt0x on 2011-06-30
Hi, 
    Completely new to Ubuntu, had it less than 48 hours but I'm starting University in October so I'll have to get used to it so excuse my basic questions.

I have a VPN account and have been running it perfectly on windows without any problems but I deleted my windows OS because I wanted to force myself to learn a Linux OS. I have installed the configuration package through the terminal and have followed this guide exactly

[http://www.ibvpn.com/billing/knowledgebase/35/OpenVPN-setup-on-Linux-graphical-Network-Manager.html](http://www.ibvpn.com/billing/knowledgebase/35/OpenVPN-setup-on-Linux-graphical-Network-Manager.html)

The VPN was giving me a no secrets error to start off but I managed to fix and now it connects for about 40seconds but whilst it is connected, the internet is completely useless and I can't get on anything... It then disconnects after 40 seconds saying it has failed.

I installed firestarter to see if I could tweak it there to work but it was beyond me and I could also see from the data being sent that none of it was going through tap0 whilst the VPN was connected..

any ideas?

Thanks

---

### Post by pawhtiobo on 2011-06-30
I also use OpenVPN, at the beginning i had some trouble to put it working in Ubuntu...

1- Remove "Firestarter", because it's an additional kind of firewall and we don't want more things messing with the connection....

2- Has i can see in the online manual you provided, in the **8** step, the picture bellow has an option "use custom gateway port" with **1194** greyed, activate that option and leave the default port (1194).

3- You will need do allow traffic through that specific port in Ubuntu using IPTables.


Type in terminal:


 _To allow OpenVPN:_

**sudo iptables -A INPUT -p udp --dport 1194 -j ACCEPT**

_To allow traffic to/from bridged interfaces:_

[B]sudo iptables -A INPUT -i tap0 -j ACCEPT
sudo iptables -A INPUT -i br0 -j ACCEPT
sudo iptables -A FORWARD -i br0 -j ACCEPT[/B]


4- Check if your router also accept traffic throught that port.


See ya....

---

### Post by semt0x on 2011-06-30
Hi, 
     Thanks for the reply.. It wouldn't allow me to select a port on the VPN settings but I managed to open the port up like you said and it just seemed to work. Nice satisfying feeling thanks again

---

### Post by pawhtiobo on 2011-07-01
Glad we could help :)

You can mark the thread as solved using the "Thread tools".


See ya....

---

