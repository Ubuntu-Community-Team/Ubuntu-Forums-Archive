---
title: "Wrong DNS address after disconnecting from VPN"
date: 2010-03-17
forum: Networking &amp; Wireless
---

### Post by duncanmc on 2010-03-17
I updated Kubuntu from 8.10 to 9.04. After the update, I saw a problem with VPN connections. I am using an mac pro with 2 ethernet ports. Only one of them is connected to switch. I am using a static IP in my local network. The problem is that I lose dns information after connecting and disconnecting to a VPN by KVpns. 

As I am using static ip, I entered my dns server to resolv.conf file with "nameserver 192.168.128.4". My interfaces file is as follows:

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0


iface eth0 inet static
address 192.168.129.24
netmask 255.255.252.0
gateway 192.168.128.1

auto eth0

After I connect to a VPN that uses dhcp, I see that resolv.conf file is updated with the dns server of the vpn network with "nameserver 192.168.128.1". That's ok. However, after I disconnect from the vpn connection by KVpns, I could no longer connect to servers outside my network. I saw that resolv.conf still has the dns server address of the vpn with "nameserver 192.168.128.1" even though I disconnected from vpn. I could connect to internet after manually changing resolv.conf file to "nameserver 192.168.128.4". 

Is this a bug or expected result? I don't remember such a problem with Kubuntu 8.10. Shouldn't KVpns restore the original dns address of my network after disconnecting? Why does it keep the dns address of the vpn connection?

---

### Post by suseendran.rengabashyam on 2010-03-17
Hi,

You can follow this thread for more details

[http://ubuntuforums.org/showthread.php?t=1055929](http://ubuntuforums.org/showthread.php?t=1055929)

Hope this helps.

---

