---
title: "Dlink DW-140 issue:Not able to set ESSID and not ping the gateway"
date: 2008-12-27
forum: Networking &amp; Wireless
---

### Post by Ravi_Chobey on 2008-12-27
Hi All,

I am having Dlink DW-140,ralink 2870 based Wireless USB adapter.I have followed these steps for usting it:

insmod public/rt2870sta.ko /*loading the device driver*/
ifconfig ra0 up
iwlist ra0 scanning


*if have key
iwconfig ra0 essid "Dlink" key "0222993370"

4. create ifcfg-ra0, command line below:
vi /etc/sysconfig/network-scripts/ifcfg-ra0

insert below:

DEVICE=ra0
BOOTPROTO=dhcp
ONBOOT=no
TYPE=wireless
MODE=Managed
RATE=54M

5. command line below:
ifconfig ra0 up
route add default gw 192.168.1.1

I am facing problems while setting the Essid i.e "Dlink".When i am running "iwconfig" command,i am only able to see ESSID "". I am not able to ping my the gateway IP address.

Please support me in solving this issue.

Regards,
Ravi Chobey

---

