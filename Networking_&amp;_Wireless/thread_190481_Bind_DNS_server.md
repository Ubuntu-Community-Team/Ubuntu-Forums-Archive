---
title: "Bind DNS server"
date: 2006-06-06
forum: Networking &amp; Wireless
---

### Post by cheers on 2006-06-06
How can i install and configure an DNS (bind9.3.2) ?

---

### Post by unicycler on 2006-06-06
Easiest would be to use the synaptic package manager. Search for Bind and select and apply the version you would like to install. Unfortunately configuration is not so easy. You will need to open your favorite text editor and configure /etc/named.conf and set up necessary data files in /var/named.

---

