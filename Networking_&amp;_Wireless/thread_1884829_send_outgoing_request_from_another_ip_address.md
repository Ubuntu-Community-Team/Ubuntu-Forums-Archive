---
title: "send outgoing request from another ip address"
date: 2011-11-22
forum: Networking &amp; Wireless
---

### Post by enigma_hr on 2011-11-22
hi everybody

i have found a problem,i need to send my http request from my server secondary ip address,and my server just has to ips but it has one interface ,when i open my interfaces file it show below content,but im new in ubuntu,i dont know how can i do it

iface eth0 inet static
address my.ip.add.ress
netmask 255.255.255.0
gateway 78.159.108.1
broadcast 78.159.108.255
network  my.ip.add.0


iface eth0:0 inet static
address my.second.ip.address
netmask 255.255.255.0
gateway 178.162.154.1
broadcast 178.162.154.255
network my.second.ipaddress.0


please help me

---

### Post by newbie-user on 2011-11-22
Try flushing your routing table and setting your default route to your eth0:0 settings

---

