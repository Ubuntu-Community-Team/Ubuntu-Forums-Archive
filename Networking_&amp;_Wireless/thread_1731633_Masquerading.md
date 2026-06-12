---
title: "Masquerading"
date: 2011-04-17
forum: Networking &amp; Wireless
---

### Post by drewbob on 2011-04-17
Hi all, I posted earlier about this but marked it as solved because it seemed to be working,  Unfortunately, it isn't anymore.  

This is the setup:

I've got a wireless router which my laptop is connected to on wlan0, with an ip address of 192.168.1.2.  This is the internet connection for the laptop.  I've then got an ethernet card which I've given an ip address of 192.168.2.1, (subnet mask 255.255.255.0, and default gateway is 192.168.1.1 [is that right for masquerading?]).  This connects via a crossover cable to a desktop computer with the ip address 192.168.2.2, and I'm trying to get this one to connect to the internet via the laptop.

I've been looking at several guides, and basically, on the laptop (the host) I've put in the following commands:

iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE
iptables -A FORWARD -m state --state ESTABLISHED,RELATED -i wlan0 -o eth0 -j ACCEPT
iptables -A FORWARD -i eth0 -o wlan0 -j ACCEPT

echo 1 > /proc/sys/net/ipv4/ip_forward

that final one I'm guessing is just some binary "forward or not" switch.

Then, on the desktop (the client) I've added the laptop as the default gateway:

route add default gw 192.168.2.1

And I've put (this one I'm really not sure about):
nameserver 192.168.2.1

 in /etc/resolv.conf

I have tried a few combinations of that but I'm not really sure what's supposed to go in there.

Couple of other things to note: 

1)  The machines can ping each other.

2) There is a dodgy entry which appears both in the routing table and /etc/networks on the desktop (client).
it's this link-local 169.254.0.0 network.  Also 192.168.2.0 doesn't appear in /etc/networks, should it? 

3) One guide told me to ensure this line was in /etc/sysctl.conf 
net.ipv4.ip_forward = 1

Any input would be greatly appreciated.  Is this setup correct, and if not, why not?  I'm particularly confused about the /etc/resolv.conf file and what the DNS address for the desktop should be.  Is there anything I've missed/still to do?  

I'd also like to know what other files are involved in the ip_forwarding, so I can double check everything, and finally also, which services, if any, need to be  restarted for the ip forwarding to take effect once the settings are correct.

Thanks,

Andrew

---

