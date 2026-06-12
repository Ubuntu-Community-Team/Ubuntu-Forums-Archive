---
title: "dnsmasq hangs up modem"
date: 2010-01-01
forum: Networking &amp; Wireless
---

### Post by billsdesk on 2010-01-01
I am trying to use XUbuntu 9.10 as an Internet gateway on an ancient Micron Transport ZX laptop, and am having a few problems. I am using a USB modem to connect to Verizon and a Broadcom wireless for the internal network. I am using dnsmasq for connection sharing. DHCP works just fine. DNS works just fine.

Without the wireless connect, I have a stable Internet connection. When I enable the wireless connection, and start a browser on another machine, I have problems. The browser makes the connection, and then hangs. At some point, the modem hangs up and then redials. Outside of DNS, which dnsmasq handles, anything forwarded to the Internet causes the modem to eventually hang up. I disabled ufw, and the problem remains.

I tried substituting wicd for Network Manager to eliminate that potential conflict. Alas, wicd refuses to recognize the Broadcom card since I use ndiswrapper. Haven't solved that problem either. Network Manager always recognizes the WiFi card, but sometimes ignores the USB modem. I had to resort to using sudo nm-connection-edit to edit the connections, since Network Manager always gives me an authorization error.

I changed to wicd, which removed Network Manager, and got it to recognize the wireless card. Used wvdial to start the modem. Restarted dnsmasq and still have the same problem.
Any ideas?

:confused:

---

### Post by billsdesk on 2010-01-01
It took a bit of searching the Internet and testing, but I got it to work. The solution I used was to get rid of the Network Manager and disable ufw with the command: sudo ufw disable.

In place of the Network Manager I installed wicd. Since the Belkin card I use has a Broadcom chip, I use ndiswrapper to wrap the Windows driver. wicd wouldn't automatically find the card, so I had to manually add it the preferences section.

I use wvdial to connect the USB modem to Verizon. To avoid having to manually dial the connection, I added the following lines to /etc/network/interfaces:
auto ppp0
iface ppp0 inet wvdial

For DHCP and DNS services, I used dnsmasq. It is a bit of work to go through all  the configuration options. There is one critical change. I set resolv-file=/etc/ppp/resolv.conf.

Since UFW does not provide NAT services, I used FireStarter. I had to add policies for DNS and DHCP for the local lan. i set the configuration option to start firestarter after ppp0 was available. In addition, I had to add the the following line to /etc/firestarter/user-pre:
$IPT -A INPUT -i $INIF -p udp -s 0.0.0.0 --sport 68 -d 255.255.255.255 --dport 67 -j ACCEPT

For IP forwarding, I also made the following changes to /etc/sysctl.conf:
net.ipv4.ip_forward=1
net.ipv4.conf.default.forwarding=1
net.ipv4.conf.all.forwarding=1

---

