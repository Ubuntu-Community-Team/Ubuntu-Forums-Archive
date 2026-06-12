---
title: "Configuring LAN-Internet through wired connection"
date: 2010-08-17
forum: Networking &amp; Wireless
---

### Post by sunnyengineeer on 2010-08-17
Hello,
           I've installed Ubuntu 10.04 on my classmate's Lapie after he got frustrated with Windows 7:)
Everything is fine except LAN connection wired one...

Can anyone tell me how to confiure that..& from where ?Like his IP addressis 192.168.68.10 with subnetmask 255.255.255.0

Plz guide me for this...Bcz many of my fellow hostelmates are for Ubuntu if I configure it out...



Thnx
Sunny Sharma

---

### Post by ercferret18 on 2010-08-17
do you need to assign a static ip address?

---

### Post by Iowan on 2010-08-17
Network Manager can be used to configure DHCP and/or static addresses. From a terminal (Applications>Accessories>Terminal), **ifconfig -a** should show if the machine has an IP address.

Otherwise, it might be helpful to know the laptop brand/model and interface chipset. Much of this information is also available via terminal: **sudo lshw -C network**

---

### Post by sunnyengineeer on 2010-08-18
Hello,
             I need to assign a static IP to that laptop...
Can somebody plz help me out for this...??

Thnx
Sunny Sharma

---

### Post by nnamdi on 2010-08-18
hey to assign a static ip address you can do it from system > pref> network connections
 then under the WIRED TAB you should see your eth0 card click on it then edit and put in your parameters

---

### Post by dineshs on 2010-08-18
Right-click on the NM icon(two opposite arrows on top right) and then click on Edit Connections. 
Select the tab, wired 
select the ethernet connection you want and click edit(you can add the ethernet connection if not listed) 
select ipv4 
method-manual 
address 192.168.68.10
mask 255.255.255.0 
gateway 192.168.68.1 
then [COLOR="Blue"]hit enter [/COLOR]
DNS 4.2.2.1
then click apply 
Note:IP ,gateway and DNS-substitute your values

---

