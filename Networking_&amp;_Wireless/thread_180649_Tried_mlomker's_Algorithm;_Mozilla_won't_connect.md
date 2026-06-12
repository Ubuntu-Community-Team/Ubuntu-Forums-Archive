---
title: "Tried mlomker's Algorithm; Mozilla won't connect"
date: 2006-05-22
forum: Networking &amp; Wireless
---

### Post by dnaxy on 2006-05-22
Breezy just installed with kernal 2.6.12-9-386 on second Sempron 2800 box. Use ISP Comcast which claims DHCP. Dual XP and Mandrake work fine with first box on same cables.

Went through mlomker's fine algorithm. mii-tool eth0 shows link OK. ifconfig eth0 shows no inet adddr. Looked at drivers with lspci, etc. Found two drivers, 8139too and 8139cp. Tried ifconfig eth0 up. Still no inet addr using ifconfig.
route -n shows no destination, gateway or genmask addresses. Pinging shows url not recognized. Tried sudo dhclient eth0 and got Internet Systems Consortium DHCP Client v 3.0.2. Site 0: unknown hardware address type 776.
Listening on LPF/eth0/00:14:2a:da:c6:b8. Sending on ditto. Sending on socket/fallback. DHCP Discovers on eth0 255.255.255.255, port 67 interval 8,14,15,21,3 (whatever this means). No DHCP offers received. No working leases in database-sleeping."

I did the ipv6 removal thing (I think). cat /etc/network/interfaces showed auto lo, hotplug stuff and network 24.7.80.0, broadcast 24.7.87.255 and dns nameserver 68.87.76.178.

Looking at ifconfig errors showed RX errors @ 127,000 and TX errors 89. Repeated after one hour showed RX 16,000 and TX 17. 

Reader OMJD's thread suggesting telneting google. Mozilla did not recognize. 

I did the /etc/modprobe.d/aliases thing and got rid of net-pf-10 ipv6 and changed them to off. TIA, I remain quite stumped or stupid.

---

### Post by dnaxy on 2006-05-24
The answer to all my confusion was that I did not recycle my cable modem.

 I then did it exactly as mentioned in the manual. My ISP, Comcast, does NOT pay any attention to the MAC, or hardware, address. This is what I feard. Viz: they could detect a new NIC card in my new machine and hence charge for it.

---

