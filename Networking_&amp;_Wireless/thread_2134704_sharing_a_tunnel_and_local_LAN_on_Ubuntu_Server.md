---
title: "sharing a tunnel and local LAN on Ubuntu Server"
date: 2013-04-11
forum: Networking &amp; Wireless
---

### Post by Uberman on 2013-04-11
I'm pretty much a moron with regard to VPN tunneling.

However, I've successfully established an openvpn tunnel (dev tun0) on my Ubuntu Server 12.04.2 machine (standalone, not a VM).  I've also successfully bound my Transmission client to its IP address, and I have verified that all traffic goes through the tunnel.

The problem is that other processes not explicitly bound to the VPN (e.g., apache2 web server) have become inaccessible via my LAN/NAT access (as though eth0 traffic has just been blocked).  If I disable the VPN, then my router port-forwarding to the LAN IP of the machine works correctly.

So, I'm looking to do something like (bad ASCII art time):

```
  +-------------------------+
  |  Ubuntu Server          |
  | +---------+ +---------+ |
  | | Xmission | | Apache | |
  | +---------+ +---------+ |
  |     |           |       |
  +---[tun0]------[eth0]----+
        |           |
  +.............-------------+
  |.........Router  (NAT)    |
  +.............-------------+
              |
          [Internet]
```

I tried binding apache2 directly to the IP of eth0, but it remains inaccessible through the router's port-forwarding while the tunnel is enabled.

If this is possible, I'm guessing I'm probably going to need manipulate the routing tables to make this work properly, but all the Google results I've read are pretty arcane, and I've not actually seen anything that appears to apply to my situation.

Anybody have any insights?

---

### Post by Hadaka on 2013-04-12
Hi, I probably know less about this than you do.
but i "think" iptables routing might do what you
want. check this how to link.
[http://www.fclose.com/b/linux/816/port-forwarding-using-iptables/](http://www.fclose.com/b/linux/816/port-forwarding-using-iptables/)
good luck.

---

### Post by Uberman on 2013-04-15
Thanks, Hadaka.  I'm sure I need some kind of additional configuration on the tables, but that link you provided seemed to be just as convoluted as everything else I've seen (I know it's probably a convoluted subject to begin with!).

It seems the question/subject is too advanced for this particular forum.  I'll have to check elsewhere for some help.  Thanks again.

---

