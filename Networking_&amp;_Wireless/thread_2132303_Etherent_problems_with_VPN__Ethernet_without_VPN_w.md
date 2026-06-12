---
title: "Etherent problems with VPN | Ethernet without VPN works fine | Wirless with VPN works"
date: 2013-04-04
forum: Networking &amp; Wireless
---

### Post by Fartwer on 2013-04-04
Hello ubuntuforums members, I have problems with my Ethernet Connection with Ubuntu 12.10 on my new DELL XPS.

Note: My wireless connection uses another net than the Ethernet connection does

  If I use my Etherent connection without VPN (PPTP/OpenVPN) everything works fine.  If I use my Wireless connection with VPN or without VPN (PPTP or OpenVPN) everything works fine too.
  BUT if I try to use my Ethernet connection with VPN (PPTP or OpenVPN)  it will connect, and I'm able to surf about 15 seconds. After it, I get  timeouts and after about a minute the VPN will disconnect.
  I don't know where the problem is. I would really appreciate if  anyone has a idea where the issue could be. It's really strange. On  Windows I have no problems with it, but I don't want to use it, because Ubuntu is alot of better :) 


  Thanks in advance! 
Kind Regards,

---

### Post by albandy on 2013-04-04
Only for test purposes:
Connect to the vpn through ethernet
Open a terminal and type:
sudo ifconfig vpn_iface mtu 1200

If works is a mtu problem, if not it could be a driver problem, also this can be produced by a damaged network cable.

---

### Post by Fartwer on 2013-04-04
> **albandy said:**
> Only for test purposes:
Connect to the vpn through ethernet
Open a terminal and type:
sudo ifconfig vpn_iface mtu 1200

If works is a mtu problem, if not it could be a driver problem, also this can be produced by a damaged network cable.

Hello, I have tried first the commad, and I get this back: *SIOCSIFMTU*: *No such* device
I have also tried to change the cable, but I have still the same problem.
Than have also tried to install the latest drivers of the adpater, but it seems like there is still the same problem. Any other idea? :(

---

### Post by albandy on 2013-04-05
> **Fartwer said:**
> Hello, I have tried first the commad, and I get this back: *SIOCSIFMTU*: *No such* device
I have also tried to change the cable, but I have still the same problem.
Than have also tried to install the latest drivers of the adpater, but it seems like there is still the same problem. Any other idea? :(

You've to change vpn_iface with your vpn interface name.

For example, if your vpn interface name is tap0 (usually is tap0) the instruction should be:
sudo ifconfig tap0 mtu 1200

---

