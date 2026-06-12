---
title: "ubuntu server PXE thin clients"
date: 2010-05-06
forum: Networking &amp; Wireless
---

### Post by mieze245 on 2010-05-06
Question of how to have my thins clients pick DHCP from clearOS 5.1 (which they are already doing)

and in my dhcp config on the clear box point to another ip to pick up my thin client image

(ubuntu 10 server with ltsp) 


thin clients get dhcp from clear box but how do i get them to pull the thin desktops from the ubuntu ](*,)server?



 :blink: 

so which dhcp.config do i need to it the ubuntu server or the clear os file?

---

### Post by mieze245 on 2010-05-07
ok info time

here are my dnsmasq.config files

What am I missing for the pxe pc to boot off the network and pull the image from the ubuntu LTSP

In the dnsmasq directory is a file called dhcp.conf

it reads as follows

dhcp-option=eth1,1,255.255.255.0
dhcp-option=eth1,3,192.168.222.1
dhcp-option=eth1,6,192.168.222.1
dhcp-range=eth1,192.168.222.100,192.168.222.254,12h
read-ethers



the dnsmasq.conf file reads as follows 
bogus-priv
conf-file=etc/dnsmasq/dhcp.conf
dhcp-authoritative
dhcp-lease-max=1000
dhcp-option=66,192.168.222.173 (IP of Ubuntu LTSP Server NOT RUNNING DHCP!)
dhcp-option=pxe,67,pxelinux.0
domain-needed
domain=XXXXXX.lan
expand-host
no-negcache
strict-order
user=nobody





i pulled that setup from this page

[http://www.linuxjournal.com/magazine/pxe-not-just-server-networks-anymore](http://www.linuxjournal.com/magazine/pxe-not-just-server-networks-anymore)

---

