---
title: "Can I connect to 2 VPNs at the same time?"
date: 2009-12-02
forum: Networking &amp; Wireless
---

### Post by neurostu on 2009-12-02
I have two different VPN's I need to connect to. One is so that I can  authenticate MATLAB from my university's matlab license manager. The other is for my lab's VPN so I can access my data.

Is it possible to connect to 2 vpn's at the same time, and if so how can I do it?

---

### Post by DGortze380 on 2009-12-02
> **neurostu said:**
> I have two different VPN's I need to connect to. One is so that I can  authenticate MATLAB from my university's matlab license manager. The other is for my lab's VPN so I can access my data.

Is it possible to connect to 2 vpn's at the same time, and if so how can I do it?

As long as the network addresses don't conflict.
What client do you use?

---

### Post by neurostu on 2009-12-02
I use the client that is installed when I run:
sudo apt-get install network-manager-vpnc


How do I setup the connections so I don't have conflicting addresses?

---

### Post by DGortze380 on 2009-12-03
> **neurostu said:**
> I use the client that is installed when I run:
sudo apt-get install network-manager-vpnc


I'm not familiar with that client. I assume you can just add a new connection in network manager.

> 
How do I setup the connections so I don't have conflicting addresses?

You can't really. It depends on IP address the VPN Administrators have chosen for each VPN, as well as the address on the other side of the VPN, and the addresses on your local subnet. Obviously the last one, you may have some control over, but that's all.

---

### Post by Dougie187 on 2009-12-03
I wouldn't think this would be possible. I mean, the VPN is basically a tunnel that your traffic goes through, how would your connections determine which traffic should go over which tunnel?

---

### Post by DGortze380 on 2009-12-03
> **Dougie187 said:**
> I wouldn't think this would be possible. I mean, the VPN is basically a tunnel that your traffic goes through, how would your connections determine which traffic should go over which tunnel?

kernel routing table

as long as there are no IP conflicts.

---

### Post by Grenage on 2009-12-03
Yes it will work, but as previously stated, you cant have a conflicting range; example:

Will work:
```
192.168.10.0/24
192.168.100.0/24
```

Won't work:
```
192.168.1.0/24
192.168.1.0/24
```

---

### Post by neurostu on 2009-12-05
so if one vpn is putting me on 10.43.121.0/24
and the other is putting me on 18.something I shouldn't have a problem?

---

### Post by DGortze380 on 2009-12-05
> **neurostu said:**
> so if one vpn is putting me on 10.43.121.0/24
and the other is putting me on 18.something I shouldn't have a problem?

Remote -------- VPN Tunnel --- Local
192.168.0.0 --- 10.43.121.0 -- 192.168.1.0
192.168.2.0 --- 10.18.0.0 --------^


If any of those conflict, you'll have issues.
It's not just the IPs, you have to account for the subnets as well.

If your local is 192.168.1.0 255.255.255.0
and the remote is 192.168.2.0 255.255.0.0
You'll have issues. 

There are endless combination's. You just have to try and see I suppose. If you can post all the info (if you have access to it) we can predict if you'll have conflicts.

---

