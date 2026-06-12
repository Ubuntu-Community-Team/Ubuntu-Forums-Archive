---
title: "[network] Cross connectivity problem?"
date: 2012-01-08
forum: Networking &amp; Wireless
---

### Post by droxy on 2012-01-08
I have two ubuntu servers, I have connected them to each other with two identical D-Link gigabit network adapters and a cross cable, for back-up tasks and such.

it used to work, and then suddenly stopped working. I was busy so never got around to fix it till now.

Here are some more info:

1. ifconfig on both servers:

> root@Aylar:/# ifconfig eth2
eth2      Link encap:Ethernet  HWaddr 5c:d9:98:45:81:63
          inet addr:192.168.202.1  Bcast:192.168.202.255  Mask:255.255.255.0


> root@Snoop:~# ifconfig eth2
eth2      Link encap:Ethernet  HWaddr 5c:d9:98:45:81:64
          inet addr:192.168.202.2  Bcast:192.168.202.255  Mask:255.255.255.0


netdiscover -i eth2 -f

netdiscover shows:


> From SNOOP:

   IP            At MAC Address      Count  Len   MAC Vendor
 ----------------------------------------------------------------
 192.168.202.1   5c:d9:98:45:81:63    01    060   Unknown vendor


netdiscover ruunning on AYLAR, shows nothing

netdiscover -i eth2 -r 192.168.202.0/24 ==> nada!
netdiscover -i eth2 -f ==> nada!


will some one please point me to the right direction to get around this? what would the problem possibly be?

---

### Post by doas777 on 2012-01-08
well, it seems that snoop can see aylar, so its partly working. can snoop ping aylar?

do you get anything when running this from aylar?
```
arp -a
```

does lshw show the same driver in use on both ends?
```
sudo lshw -C network
```

do you have ethtool installed? if so, check it to see the duplex mode, link type, link status, etc. 
```
sudo ethtool eth0
```

last, do you have ufw installed and configured? if so, do you see any messages in the kernel log (/var/log/kernel.log) related to dropping packets?
 
are there any rules show that would block the packets?
sudo ufw status

good luck

---

