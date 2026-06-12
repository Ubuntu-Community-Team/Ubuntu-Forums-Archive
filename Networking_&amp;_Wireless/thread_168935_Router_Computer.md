---
title: "Router Computer"
date: 2006-05-01
forum: Networking &amp; Wireless
---

### Post by jumanji on 2006-05-01
I'm trying to set up a routercomputer(old 233mhz computer), but i dont have a hubb or a switch to attach to it. So my plan was to use networkcards on the free pci slots inside the routercomputer so i can connect more computers to it..

like this:

ISP-->eth0-pci1-ROUTERCOMPUTER..

ROUTERCOPUTER-pci2--eth1--192.168.0.1-->computer 1(workning)
ROUTERCOPUTER-pci3--eth2--192.168.1.1-->computer 2(not workning)
ROUTERCOPUTER-pci4--eth3-->computer 3(not used)
ROUTERCOPUTER-pci5--eth4-->computer 4(not used)

I have managed to set up a ubuntu(5.10) server install(+ ipmasq and dnsmasq) with a firewall script(automade at: [http://easyfwgen.morizot.net/gen/](http://easyfwgen.morizot.net/gen/)) to work with computer 1(eth1) on my private net. 
My problem now is how do i get computer 2 through the firewall?? In iptables it only has info about my first internal net(192.168.0.1) and if i change(or add) that info to eth2:s info(192.168.1.1) it "takes over" and 192.168.0.1 part "dies".. 

in iptables, this is what i found:

# Local Interface Information
LOCAL_IFACE="eth1"
LOCAL_IP="192.168.0.1"
LOCAL_NET="192.168.0.0/24"
LOCAL_BCAST="192.168.0.255"
  
Can i add eth2 info here, in some way??

---

### Post by mips on 2006-05-02
[http://ubuntuforums.org/showthread.php?t=111972](http://ubuntuforums.org/showthread.php?t=111972)

---

