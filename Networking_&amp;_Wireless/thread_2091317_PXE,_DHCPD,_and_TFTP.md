---
title: "PXE, DHCPD, and TFTP"
date: 2012-12-04
forum: Networking &amp; Wireless
---

### Post by 0xicl33n on 2012-12-04
Im TRYING to setup a [Diskless Boot Cluster]("https://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide")


Everything is setup, including the mini hardy fs which i can CHROOT into, it all all works perfectly! Ive followed all of the instructions in the guide above, everything is installed. Only thing is, this is a guide built for an older version of ubuntu so when i it says

[I] "
DHCP is what will allow the nodes to get IP addresses  from the server. We want to set up and configure a DHCP daemon to run  on the server and give IP addresses only to nodes it recognises, so we  will tell the daemon their MAC addresses. 
[/I] 
[LIST]
[*]*First install the DHCP server package with aptitude or apt-get, as root: *
[/LIST]
[I]
# aptitude install dhcp3-server    "
[/I]

There is no dhcp3-server for ubuntu 12, it instead installs isc-dhcp-server, which i CANNOT get to talk to my nodes whatsoever!

The /etc/default/tftp-hpa points where it should, i dont understand which freaking configuration file i should be using for dhcpd cause it seems like theres 3 different f**king DHCPD's installed.It doesnt really give me any errors , doesnt say anything is wrong, its just, when i boot a node, it says 

BOOTFILE NOT RECEIVED!

and then just boots windows. Someone needs to UPDATE THIS GUIDE. I have yet to even install kerrighed cause i want to make sure my cluster works before they share a kernel together! and so far IT ISNT!!!

HELP PLZ!!

---

