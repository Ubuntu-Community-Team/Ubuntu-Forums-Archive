---
title: "Ubuntu ICS to Windows"
date: 2010-02-07
forum: Networking &amp; Wireless
---

### Post by KaiserG on 2010-02-07
[Ubuntu 8.04 'Hardy Heron']
Hello people, I'm posting again, this time I've been trying since yesterday to share an internet connection to a Laptop which has MS Windows XP installed in it via Ethernet.
This ubuntu machine connects through a ppp interface. This is the summary of networking devices:
ppp0 (ppp interface)
eth0 (LAN adapter, connected to the laptop)
eth1 (LAN adapter, connected to the ppp modem/router)

I've been able to manage through the DHCP server and the laptop gets its IP as I configured it:
10.0.0.1 (this computer, the default gateway for the laptop)
10.0.0.250 (the laptop gets this ip when it connects, not sure if this should happen, but everytime it connects it never changes. However, is in the range of the firestarter DHCP settings so that should be ok)

After it connects. I've tried to navigate on internet but theres no response from the web. I've tried to do a #ping <ip> on the MS Win cmd and the ping packets are sent and theres response from them. So I don't really got whats wrong. There's where I need help.
Another thing, the connection from the Windows machine shows packets sent but none received (the only time when some packets are received is when the DHCP interacts)

Sorry all for the approximate english. Thanks in advance I really appreciate the support you all give to us on this forum.

---

### Post by Iowan on 2010-02-07
[Here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is an ICS help page. If you can ping the router from the client machine, the next step would be to ping internet by IP address (try 74.125.95.104).

---

### Post by KaiserG on 2010-02-08
Iowan, thanks for the reply. With the ping I meant that I can ping the internet, but I am unable to navigate.
And for the web, I went to that one and did what it says. I've checked like 4 different ICS guides and nothing worked out. The most far I could go is the current state in which I am. Able to ping internet but explorer doesn't show any page. Maybe theres something with the dns, Im using the OpenDNS from the web u linked to me. Are they working? I've always had problems with DNS learning.

---

### Post by Iowan on 2010-02-08
What are results (from a terminal) of **route -n**, and what is in */etc/resolv.conf*?

---

### Post by KaiserG on 2010-02-08
#sudo route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
200.51.241.179  0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
10.0.0.0        0.0.0.0         255.0.0.0       U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0

/etc/resolv.conf
nameserver 200.63.155.57
nameserver 200.63.155.185
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   6142
#
### END INFO

Thanks

---

### Post by Iowan on 2010-02-08
Interesting - there's no default gateway listed (no route to the internet). I'll need to look up what the "H" means...

("H" means target is a **host**)

---

### Post by KaiserG on 2010-02-09
If of any use, my computer connects without problems from the PPP interface. And it looks like the Windows machine has response from WAN ips such as Goggle for example. But never loads the web from the explorer. From there, it looks like the machine were completely disconnected.

---

