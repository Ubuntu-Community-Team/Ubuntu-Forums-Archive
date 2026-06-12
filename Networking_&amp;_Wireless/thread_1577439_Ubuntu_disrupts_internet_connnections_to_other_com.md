---
title: "Ubuntu disrupts internet connnections to other computers"
date: 2010-09-18
forum: Networking &amp; Wireless
---

### Post by El Dragon on 2010-09-18
While using Ubuntu two other computers lose their connection. One (main) is connected to the modem, other from the switch to the wireless router, and the one with ubuntu wired via switch. Currently connected with Windows 7, other two are connected. Once  booted into Ubuntu rest of the computers disconnect?

---

### Post by Iowan on 2010-09-18
All interfaces involved (wired/wireless) have unique IP addresses?

---

### Post by El Dragon on 2010-09-18
> **Iowan said:**
> All interfaces involved (wired/wireless) have unique IP addresses?

 ...well  IP Lookup website shows from the each computer the same Ip address?!

---

### Post by El Dragon on 2010-09-19
and DHCP is enabled on each computer, but not sure my aging modem is supporting it, and not sure if I should manually assign IP addresses to each computer..? So you guys think it is an 'addressing' issue? Why isn't with the Windows??

---

### Post by puppywhacker on 2010-09-19
Sounds indeed like an ip-addressing issue. Ancient modems are rarely the culprit. And from your story about the network I would say every computer is in the same lan.

Sounds more like you are running a dhcp-server on the linux system, or the avahi reconfigures the ip-address or dns server, 

from a terminal run the following commands and report back
ifconfig
cat /etc/resolv.conf
service dhcp3-server status
service avahi-daemon status
avahi-browse -a -r -t

---

### Post by Iowan on 2010-09-19
> **El Dragon said:**
> ...well  IP Lookup website shows from the each computer the same Ip address?!

An eIP lookup website will return the IP of your router/modem - not necessarily the IP of the individual machine. **ifconfig** (or ipconfig on Windows) one each machine should provide the local address.

---

### Post by El Dragon on 2010-09-19
> **Iowan said:**
> An eIP lookup website will return the IP of your router/modem - not necessarily the IP of the individual machine. **ifconfig** (or ipconfig on Windows) one each machine should provide the local address.

this time it shows different ip's...

---

