---
title: "VirtualBox networking config on a 8.10 guest running 9.04 host"
date: 2009-10-21
forum: Networking &amp; Wireless
---

### Post by dubref on 2009-10-21
How should one activate networking on a Virtualbox Ubuntu image?

Host: Ubuntu 9.04 running VirtualBox OSE 2.14
Network Adapter: Realtek RTL8111/8168B 
static IP 192.168.0.99 netmask 255.255.255.0 gw 192.168.0.1

Guest: Ubuntu 8.10
Adapter 1:  PCnet-FAST III (host interface, eth0)

Image loads, network card shows, networkmanager tries to grab IP address via DHCP and fails(presumably for the lack of DHCP server...)

On a hunch, I setup guest IP to a unused address (say 192.168.0.101, mask 255.255.255.0, gw 192.168.0.1), this does nothing of note(I can't ping gateway, etc), although guest *ifconfig* shows this 192.168.0.101 address.

I tried setting gw to 192.168.0.99 although that didn't seem sensible either. 

 From what I understand, one does not need to worry about bridging and playing around interfaces anymore, which is what one had to do with earlier VirtualBox versions.

What would be a proper way to setup?

---

### Post by compiledkernel on 2009-10-21
[http://gwos.org/udsf/doku.php/software:virtualbox](http://gwos.org/udsf/doku.php/software:virtualbox)

That should provide some proper guidance.

---

### Post by dubref on 2009-10-22
Thanks for the reply!

The guide provided a good starting point and gave me a clue. :)

I simply had to select NAT instead of Host Interface in VirtualBox settings for the guest. 

Now, at least, simple internet access works.

---

