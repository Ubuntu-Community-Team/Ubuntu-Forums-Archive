---
title: "obtaining ip address from mac address"
date: 2010-10-06
forum: Networking &amp; Wireless
---

### Post by mastupristi on 2010-10-06
In my job I use some ethernet embedded devices. They take an ip address from dhcp server or auto ip. I only know mac address.
How can I obtain ip from mac address? In other words I need a rarp packet generator.

thanks

---

### Post by gordintoronto on 2010-10-06
The mac address is built into your network adapter, it never changes. Your IP address can be anything. Mac address and IP address are not related.

Right-click on your network icon and select "connection information." Part of the information is your IP address.

---

### Post by BkkBonanza on 2010-10-06
You can use the arp cache.

eg.
cat /proc/net/arp |awk '/00:d0:da:00:37:98/ {print $1}'

It only knows what has already been discovered though so you would have to initiate some contact to a specific IP. Probably using ping would be easy but whatever you have available in your situation will work.

[noparse]ping -b <broadcast address> [/noparse]

can be used to scan the network and fills your arp cache. (Which only works if the machine responds to pings, otherwise maybe nmap is useful for this as it fills the cache too)

There probably is a more direct command that simply returns you the result of the arp request and certainly if you're coding yourself then some system call will do it. I know rarp used to do it but apparently it's history now.

---

### Post by mastupristi on 2010-10-07
I know that mac and ip address are not related.

This embedded device does not have video output or keyboard/mouse input. Does not have any console.
Is like "computer-in-a-socket".

I plug the ethernet cable in it and it takes an ip address from dhcp (obviously I do no have access to dhcpd logs).
At this point I need to "discover" this embedded device asking in broadcast "who has <embedded device mac address>?". It should answer "Am I with <ip address>"
This is done by RARP, isn't it? but RARP is get obsolete. It is replaced by dhcp.

So my question is: how can I use dhcp to discover ip address of this embedded device knowing only his mac address?

thanks

---

### Post by robert_pectol on 2010-10-07
Assuming you have a Linux box on the same network as the embedded device, you can run the following command to query the Linux box's arp cache for an entry with the MAC address in question.  If the Linux box has heard from it, there should be an entry in its ARP table.
```

arp | grep <mac_address> | cut -d ' ' -f1

```
That **should** give you the IP address associated with the device.  If it returns a hostname instead of an IP, simply do a host lookup on the name.  Ex:
```

host `arp | grep <mac_address> | cut -d ' ' -f1`

```

***note***
After re-reading the thread, I realized I've only presented another way of doing the same thing BkkBonanza suggested.  Anyway, the broadcast ping is a good suggestion.  Obviously it should be run before querying your box's ARP cache.  A simple one-liner could be:
```

ping -b -c1 -w1 <broadcast_address> > /dev/null 2>&1

```
That will send only one ping and will wait for only one second before timing out, and then it'll silently exit.  A simple script could be put together to combine it all.  You could then present the MAC address as an argument to the script.  Just use $1 for the MAC address within your script.

---

### Post by BkkBonanza on 2010-10-07
Robert has a nicer quiet version of the ping. 
So just combine those two lines and you're done. Example script file, 

```
#!/bin/bash
ping -b -c1 -w1 192.168.0.255 > /dev/null 2>&1
ARG="/$1/"
cat /proc/net/arp |awk $ARG' {print $1}'
```

You may find that your embedded device does not respond to pings. In that case you could use nmap but it would be slower.

```
#!/bin/bash
nmap -sT -PN 192.168.0.0/24 > /dev/null 2>&1
ARG="/$1/"
cat /proc/net/arp |awk $ARG' {print $1}'
```

As far as I know DHCP cannot be used for a reverse lookup.

---

### Post by rico_tux on 2010-10-22
I think this is what you was looking for [http://www.habets.pp.se/synscan/programs.php?prog=arping](http://www.habets.pp.se/synscan/programs.php?prog=arping), don't know way mac pinging is not supported in Ubuntu's arping but after installing this i was able to run.

```
sudo arping -c 1 00:26:4a:83:34:94
```
and it respondent whit :

```

ARPING 00:26:4a:83:34:94
60 bytes from 192.168.2.15 (00:26:4a:83:34:94): icmp_seq=0 time=297.670 msec

--- 00:26:4a:83:34:94 statistics ---
1 packets transmitted, 1 packets received,   0% unanswered (0 extra)

```

hope it was of any help :)

---

