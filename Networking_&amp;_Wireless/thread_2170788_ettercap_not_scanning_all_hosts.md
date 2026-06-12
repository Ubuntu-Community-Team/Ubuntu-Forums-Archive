---
title: "ettercap not scanning all hosts"
date: 2013-08-27
forum: Networking &amp; Wireless
---

### Post by Praveen_Sampath on 2013-08-27
I tried running running ettercap as follows:

```

sudo ettercap -i eth0 -Tq -M arp:remote,oneway -w out.data // /10.8.40.250/

```

But ettercap is able to add only 2 (sometimes 1) hosts to the hosts list.

```

Randomizing 8191 hosts for scanning...
Scanning the whole netmask for 8191 hosts...
* |==================================================>| 100.00 %


1 hosts added to the hosts list...


ARP poisoning victims:


 GROUP 1 : ANY (all the hosts in the list)


Starting Unified sniffing...




Text only Interface activated...
Hit 'h' for inline help

```

Why is it only printing group 1?

If I try to poison a particular host,

```

sudo ettercap -i eth0 -Tq -M arp:remote,oneway -w out.data /10.8.41.202/ /10.8.40.250/

```

It works.

my ip: 10.8.57.121     subnet mask: 255.255.224.0

I was able to run the exact same thing some time ago, add 20-30 hosts and successfully ARP poison most of them.
What am I doing wrong now?

---

### Post by sanderj on 2013-08-27
FWIW:

I installed ettercap-graphical, and I'm able to see other hosts' connections. So ... maybe you can check whether ettercap-graphical on your system sees other connections too?

---

### Post by Praveen_Sampath on 2013-09-03
Thank you for replying.

I tried it with the graphical interface, but there too I am unable to add any hosts to the hosts list. Only one host gets added, although I am certain that there are at least 20 active machines on the LAN. I am also able to ping hosts, but they don't show up on ettercap's scan.

How does ettercap scan for hosts? Is there any way by which a gateway could detect and prevent ettercap from scanning for hosts on the local network?

Thanks.

---

