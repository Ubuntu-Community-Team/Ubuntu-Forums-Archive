---
title: "Cannot connect to secure network"
date: 2006-06-04
forum: Networking &amp; Wireless
---

### Post by cemptor on 2006-06-04
managed to get my USB 802.11g adapter recognized and working with ndiswrapper (out of box version) with the 386 version of Dapper. However, cannot connect to any network which is not open. Am able to connect to an open network.

Trying to get wpa working (which is what my home network uses).

](*,) 

Tried using wpa_supplicant following the debian instructions on editing /etc/networking/interfaces, but no success. 

was getting an error message on dmesg syaing something about not being able to use ipv6. So I disabled ipv6.

No luck.

Tried using WEP, but no success there either. 

in both cases, my dhclient fails to get a an ip address, saying "no DHCPOFFERS".

Please help.

---

### Post by cemptor on 2006-06-05
I updated the version of ndiswrapper to 1.16 and managed to authenticate to my router using wpa_supplicant with a WPA-PSK key, 

I can log in to the router and see the computer attached, and even make configuration changes to it.

However I can't seem to connect to any sites or even ping the router. So I guess I am not getting any help from the DNS server or unable to reach it.

Thanks for help in advance

---

