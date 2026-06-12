---
title: "Dns"
date: 2006-04-20
forum: Networking &amp; Wireless
---

### Post by pokerface on 2006-04-20
hello ppl. when using the gui ubuntu i was able to add a dns for my school network and it would work online! however now that i decided to use just the server option because i have an other computer on this network i cant seem to find where i input this dns to get my computer to get online! im able to ping others on the network but when i ping google.com it tells me that the network is unreachable! could anyone direct me or tell me how to fix this? ty in advanced


forgot to mention im using a static ip! not DHCP

---

### Post by Gcool on 2006-04-20
Just open /etc/resolv.conf with your favorite text-editor, and add/change:

nameserver ip of your dns server

---

### Post by pokerface on 2006-04-21
hey thanks for the response however it didnt work! im still not able to connect to the internet! all i know is that when it was in gui mode i would go to the the networking admin window and put 'static: 192.168.0.10', 'submask:255.255.255.0','default gateway:192.168.0.1' then clikc on the dns tab and put 209.82.33.212 and then B O O M the internet would work! i dont see y this didnt work in server mode? is there anything im missing?

---

### Post by Gcool on 2006-04-21
Try checking the following:

* In the file /etc/network/interfaces you should have something like:

iface eth0 inet static
adress 192.168.0.10
netmask 255.255.255.0
gateway 192.168.0.1

* In /etc/resolv.conf you should have something like:

nameserver 209.82.33.212

After you've done these settings:

* ifdown eth0 (I'm assuming in these examples that your networkcard is eth0)
* ifup eth0

See what this gives as a result.

---

