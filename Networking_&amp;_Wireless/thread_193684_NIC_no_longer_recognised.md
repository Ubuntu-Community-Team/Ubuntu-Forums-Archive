---
title: "NIC no longer recognised"
date: 2006-06-10
forum: Networking &amp; Wireless
---

### Post by LaundroMat on 2006-06-10
Hi,

Since I've moved my Ubuntu to another place, the ethernet nic inside is no longer recognised/loaded.

lspci gives "Ethernet Controller: Winbond Electronics Corporation: Unknown Device 0900 (rev 0b)"

ifconfig only shows "lo", no eth0.

/etc/init.d/networking restart gives:
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.

Anyone? Thanks in advance...

---

### Post by LaundroMat on 2006-06-10
Small update: the NIC works fine, as I have been able to access the network via a Windows box' connection sharing. 

Now.. That box gave my Ubuntu PC the adress of 192.168.0.64, while my router gives out adresses starting from 192.168.**1**.64. Could there be a reason why eth0 is not configured when connected to the router, while it does get its IP adress when connected to another machine?

---

### Post by Slim Odds on 2006-06-10
[quote=LaundroMat]Small update: the NIC works fine, as I have been able to access the network via a Windows box' connection sharing. 

Now.. That box gave my Ubuntu PC the adress of 192.168.0.64, while my router gives out adresses starting from 192.168.**1**.64. Could there be a reason why eth0 is not configured when connected to the router, while it does get its IP adress when connected to another machine?[/quote] 
A little explanation of your configuration would be nice.

If your interface is setup as a DHCP client, it will take an address from whatever address range the DHCP server is giving.

---

### Post by LaundroMat on 2006-06-11
It's indeed a (wired) DHCP client. The router is configured as to give out adresses in the range of 192.168.1.64 - 192.168.1.254. There is one wireless client. I'm beginning to believe there is some IP conflict, as the wireless client previously had 192.168.1.65 as its IP, and it's now always given 192.168.1.64. Either there's a conflict, or the Linux box simply doesn't get an IP for one reason or another.

Is there a possibility that the .64 IP adress is somehow hardwired in the Linux box? Ie, that it expects to be give 192.168.1.64 as an IP and otherwise it won't even configure eth0? In more other words, do I have to do something to make Ubuntu clear that it indeed is a DHCP client (something with which it had no problems previous to the move)?

---

### Post by LaundroMat on 2006-06-11
I tried to edit the /etc/networking/interfaces and added

auto eth0
iface eth0 inet static
address 192.168.1.110
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1

/etc/init.d/networking restart then gave me the error message "don't have all variables for eth0".

---

