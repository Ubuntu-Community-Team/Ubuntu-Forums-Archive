---
title: "DSL connection and opening ports"
date: 2009-06-20
forum: Networking &amp; Wireless
---

### Post by jenova_skill on 2009-06-20
I've completely switched to ubuntu now and I am having a few problems running programs due to unopened ports Im using a linksys wrt54g router on a dsl connection ( the Ip changes every day ) I've set it up in windows to open specific ports for programs. However on Ubuntu I am unsure how to do this. Im not to experienced on the issue and I am wondering if theres a dummy proof guide to do this?
Im trying to run Runes of magic in wine basically and it's not connecting to the server and i read it is a firewall/ port issue.
I know how to set up the ports VIA linksys router however I am unsure how to assign the IP address in Ubuntu / Ipconfig

---

### Post by DeathMetal on 2009-06-20
See if this helps.

[http://portforward.com/english/routers/port_forwarding/Linksys/WRT54G/default.htm](http://portforward.com/english/routers/port_forwarding/Linksys/WRT54G/default.htm)

---

### Post by jenova_skill on 2009-06-20
How do I tell what my IP adress is So i can set it in port forwarding?

---

### Post by cariboo on 2009-06-20
If you are going to use port forwarding, you should set a static ip address on the computer, as the ip address could change on every reboot.

Right click on the network-manager icon in the upper panel and select Edit Connections. Highlight your connection and click Edit. Enter your password when asked, the click the IPv4 tab, select Manual from the method drop down then click Add addresses. Fill in address, netmask and gateway ip addresses. Use an ip address outside the addresses assigned by dhcp. use 255.255.255.0 for netmask and gateway should be 192.168.1.1. Finally enter the dns address assigned by your isp, it should be on the status page of your router admin app. then click apply. You should now be able to forward ports without it changing for every reboot.

---

