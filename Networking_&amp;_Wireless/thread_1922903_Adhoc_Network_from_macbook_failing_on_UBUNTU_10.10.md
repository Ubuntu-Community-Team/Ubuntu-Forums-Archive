---
title: "Adhoc Network from macbook failing on UBUNTU 10.10"
date: 2012-02-09
forum: Networking &amp; Wireless
---

### Post by snif123 on 2012-02-09
Hi all,
I have an adhoc network from my macbook, it's 40-bit WEP security. Other devices(windows) connect it fine and even my mobile connects fine.
My Ubuntu 10.10 machine has problems. It never connects and just hangs trying to connect. I have installed wicd and tried it but it also gives an error when trying to validate the password. The password is **iomano** I have tried to add the password through the terminal (iwconfig eth1 key omana) but this gives error **Error for wireless request "Set Mode" (8B2A) invalid argument omano**
Any ideas on how to proceed?
PS. I connect to other WiFi APs fine. I have removed the security on my wifi now and tried to connect but still hangs..!


[UPDATE]
I have managed to do this iwconfig eth1 essid "wifiname" key s:omana
The s: translates the key into HEX from passphrase.
I then do dhclient eth1 to get an ip from the AP
I am still getting No DHCPOFFERS and the attempt times out !
Any ideas?
Thanks!

---

