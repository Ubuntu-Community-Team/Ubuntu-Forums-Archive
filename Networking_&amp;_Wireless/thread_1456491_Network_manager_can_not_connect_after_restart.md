---
title: "Network manager can not connect after restart"
date: 2010-04-17
forum: Networking &amp; Wireless
---

### Post by AKG_8 on 2010-04-17
Hi folks ..

I am having a strange problem .. my laptop works fine with a wired connection and when using that I set up a wireless network, it works fine too ... until I restart the machine .. after that it is never able to connect to the internet.

I am using ubuntu 9.10 and network manager as the wireless manager ..

Please advise ..

AG

---

### Post by Iowan on 2010-04-17
Is the (lost) Internet connection via wired or wireless?

---

### Post by AKG_8 on 2010-04-18
lost connection is wireless after restart ... wired is always good

---

### Post by BennieBlount on 2010-04-18
I had a similar problem this morning on boot - Networks Disabled. I found the answer on this forum under ""Network Disabled" after reboot" thread.

I ran this as root:

service network-manager stop
rm /var/lib/NetworkManager/NetworkManager.state
service network-manager start

This, or a variant of it, may or may not work for you. Just a suggestion, as I am somewhat new to Ubuntu.

---

