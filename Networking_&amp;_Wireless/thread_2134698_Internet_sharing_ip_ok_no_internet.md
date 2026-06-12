---
title: "Internet sharing ip ok no internet"
date: 2013-04-11
forum: Networking &amp; Wireless
---

### Post by tsukiyomi on 2013-04-11
Hi I have the next setup a win 7 computer with virtual box and ubuntu 12.0.4 as my guest machine, with two nic cards the first one as nat, the second as bridge,
in ubuntu I have done the following to share the conection:

Enabled network adapter ipv4 setting to share internet, now this gets my an ip on eth1 10.42.0.1
eth0 (nat adapter) has 10.0.2.15 and if I connect an ethernet cable on the host on the other lan computer I will get a valid 10.42.0.x ip but no route..

I also followed the next site and configured all as is the same response from both [https://help.ubuntu.com/community/Internet/ConnectionSharingDHCP3](https://help.ubuntu.com/community/Internet/ConnectionSharingDHCP3)

Ïf I disconnect the cable internet comes back again to host and guest, what am I missing.

Please some help would be great as my brain is melting, :(
Sorry If my english is wrong 
[COLOR=#000000]

[/COLOR]

---

### Post by RogerT999 on 2013-04-12
I'm also having a problem with sharing. The address 10.42.0.1 from ubuntu is given a mask of 255.255.255.0 whereas the default mask for network 10 is 255..0.0.0 effectively different networks. The equipment I'm connecting to has no option to change the default mask. Have you checked that your masks are matching.

---

### Post by tsukiyomi on 2013-04-12
Yes I have checked the masks, I was able to set up both interfaces in  255.255.255.0, is your issue the same as mine, or have you tried some different setup?

---

### Post by tsukiyomi on 2013-04-12
I got it partially to work , I had to change the virtual lan side's ip and subnet completely, on host I have this ip 192.168.220.x
on virtualbox nic 1 (nat) It has ip 10.0.2.15 255.255.255.0 netmask shared this connection and static ip on bridge nic 172.16.0.1 netmask of 255.255.0.0
now connected cord and on client pc set up static ip 172.16.0.2 same netmask..(I don't get why it was not asigned by dhcp) and Im finally able to ping 8.8.8.8 and any ip outside
but not by domain name, tried seting up static dns, in host and guest and in the same client and it did not worked, but hey its something, will continue looking.. any ideas would be nice :)

---

