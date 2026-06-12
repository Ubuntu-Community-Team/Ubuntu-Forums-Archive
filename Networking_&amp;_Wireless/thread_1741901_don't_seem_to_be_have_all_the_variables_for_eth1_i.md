---
title: "don't seem to be have all the variables for eth1 inet"
date: 2011-04-28
forum: Networking &amp; Wireless
---

### Post by matthiasba on 2011-04-28
I'm having a strange problem. I'm using Ubuntu server 10.04 LTS and I want to setup a system with 2 network interfaces: eth0 and eth1. However eth1 does not come up at boot

I have a screenshot of my /etc/network/interfaces file

I don't see what is wrong.

eth0 gets it's adress from DHCP
eth1 gets a static adress.

When i try to restart networking it quits with this message "**don't seem to be have all the variables for eth1 inet"**

Can anyone point out what I'm doing wrong? 

if i do 'sudo ifconfig eth1 192.168.3.1 netmask 255.255.255.0 up' eth1 comes up

Thanks for the info,

Matt.

---

### Post by chili555 on 2011-04-28
I wonder if it's confused simply because you misspelled 'address.'

---

### Post by matthiasba on 2011-04-29
oh man,

I could have looked for that for ages. Thank you for pointing it out. 

Matt.

---

### Post by chili555 on 2011-04-29
Does that mean it's fixed?

---

