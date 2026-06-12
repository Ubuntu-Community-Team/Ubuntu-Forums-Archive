---
title: "dhcp client not working/wep authentication failing"
date: 2009-09-27
forum: Networking &amp; Wireless
---

### Post by vpnm_87 on 2009-09-27
i use Dell studio 1535/ubuntu 9.04...

when i give wep key in network manager applet after 3-4 min its again showin the same window with my passkey entered..i tried again n again but its not connectin to my router..

it was workin fine for past two weeks..recently i tested wired connection n shared internet connection frm another laptop running Vista...after that my wireless connection not working now..


i saw output in /var/log/syslog...it was very long but it associated n authenticated fine..

but dhcp client failed to assign an ip to my laptop..i issued

sudo dhclient eth1(my wireless interface)

but its no getting assigned any IPs and i have to kill the process(dhclient)


any suggestions plz...

---

### Post by vpnm_87 on 2009-09-27
its working fine if i provide the network settings manually..
also i have to deactivate and activate the the broadcom driver everytime to make tht manual network setting work in System->Administration->Hardware Drivers....


i have no idea wats happenin..anyone provide some clarification plz...

---

### Post by vpnm_87 on 2009-09-27
now i set the IPV4 setting to "Automatic DHCP"...
then deactivate and activate "Broadcom STA driver"...
its working fine...

but after restartin my PC,dhcp client just fails to get an IP(either its in Auto DHCP or manual setting)...

i guess i found some temporary(weird) fix of deactivating and activating broadcom driver to get it working...

---

