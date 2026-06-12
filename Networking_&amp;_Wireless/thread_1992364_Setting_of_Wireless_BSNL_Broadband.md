---
title: "Setting of Wireless BSNL Broadband"
date: 2012-05-31
forum: Networking &amp; Wireless
---

### Post by Victortay on 2012-05-31
Hi,

I have BSNL broadband in India and I am using Ubuntu 12.04. The wired connection works fine. But I want to try if I can access my broadband using wireless. So I followed a guide here. [http://www.prash-babu.com/2009/05/how-to-setup-wireless-adhoc-network-in.html](http://www.prash-babu.com/2009/05/how-to-setup-wireless-adhoc-network-in.html)

When I click connect Hidden Wireless Network and choose my_adhoc (name I gave when creating wireless configuration), it says wireless network connected. But I can not access internet using wireless network. I can access internet using wired network. But if disconnect wired network and connect wireless network, I can not access internet.

Pl. help.

---

### Post by Sularco on 2012-06-01
The manual you are refering to outlines the setup of an ad-hoc wireless connection from an Ubuntu machine without Internet access to a Windows-PC with Internet access. The idea is obviously to share the Internet connection of the Windows PC with the Ubuntu PC over that unsecured hidden wireless ad-hoc connection.

Assuming that you are trying to do exactly the same, did you enter a suitable DNS server in the Ubuntu configuration as per that manual? Can you ping any IP address on the Internet from the Ubuntu machine like e. g. 208.67.222.222? If that works it would prove that the connection is active and that it in fact is a DNS related problem.

---

