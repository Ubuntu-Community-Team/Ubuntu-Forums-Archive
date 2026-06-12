---
title: "Firewall config for Ubuntu 9.10 router/server"
date: 2010-04-08
forum: Networking &amp; Wireless
---

### Post by dre12b on 2010-04-08
Three questions:
1) Do I need to install a firewall on my Ubuntu router/server (see specifics below)?
2) Is there a good out of the box firewall solution to get up and running in a hurry (without knowledge of iptables)?
3) What are good resources to learn about iptables and firewall configuration?  I'm a little frustrated with the fragmented knowledge out there in how-tos and want to learn the basics, then how to implement.

Specifics:
Did a clean install of 9.10 ubuntu server on a spare laptop with several objectives in mind: 
-1. turn the laptop into a router with a USB 3G modem (internet connection) providing internet through this machine to a wireless access point.
-2. normal desktop use with KDE
-3. home server for file sharing.
-4. when 1-3 are up and running dependably, I'll try to screw everything up by ALSO making this a media server for my home network with mythbuntu.

 I followed a tutorial and succesfully set up the routing using dnsmasq and some iptable edits.  Woohoo!  Of course, the desktop install was pretty easy, so step 2 is also taken care of.  Before moving on to steps 3 and 4, I suspect that the Ubuntu machine urgently needs a firewall, but I don't know enough to set one up and am afraid I'll tank the router setup if I tinker with the iptables in my current state of ignorance.  I'm willing to invest some time learning about firewalls and network configuration, but haven't found good learning resources.  And I'm betting I need the firewall now.  To add a sense of urgency to the matter, I'm monitoring usage on the USB 3G modem, which has a 10 GB monthly cap, and have found some inexplicable multi-GB through traffic.  

Any help will be greatly appreciated!

---

### Post by Iowan on 2010-04-08
Generically speaking...
UFW is a firewall option that comes standard. The [Server Guide]("https://help.ubuntu.com/9.10/serverguide/C/firewall.html") has some other options... Good Luck!

---

### Post by dre12b on 2010-04-09
Thanks for the tips.  I still can't figure out the firewall though.  I've got ufw and gufw installed.  When I enable ufw, internet access from the server/router machine is unaffected, but the other computers on my home network can no longer access the internet.  I added a rule using gufw to allow both kinds of traffic (tcp and udp) from the IP address of one of the machines on my network to anywhere.  Still no dice - I can't even open a webpage from that computer.  Any suggestions?  

FYI the home network is set up using instructions on this Ubuntu help [page]("https://help.ubuntu.com/community/Internet/ConnectionSharing").  I set up the internet gateway on the Ubuntu server using iptables, then created a dns/dhcp server on the same machine using dnsmasq.  This is up and running without problems.

---

### Post by Iowan on 2010-04-09
Are the other computers 'buntu boxes? You could check **route -n**  to see if they know how to get to Net. If you can successfully ping Net by IP address (try 74.125.95.99), it may be nameserver problem.  Contents of */etc/resolv.conf* should tell which nameservers to use.

---

