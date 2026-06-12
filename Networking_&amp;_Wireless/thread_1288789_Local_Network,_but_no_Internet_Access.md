---
title: "Local Network, but no Internet Access"
date: 2009-10-11
forum: Networking &amp; Wireless
---

### Post by brohism on 2009-10-11
My Ubuntu system has recently stopped communicating with the Internet.  Every other computer on my network is having no problems accessing the Internet.  The Ubuntu system works fine on the local network, including with Samba.  However, when I try to communicate with it remotely, I can't establish a connection (which used to work, with no settings being changed whatsoever on the router).  Also, I cannot ping out from Ubuntu, using either domain names or IP addresses.  How should I go about fixing this?

---

### Post by Iowan on 2009-10-11
Does gateway setting (**route -n**) still point to your router?

---

### Post by brohism on 2009-10-11
> **Iowan said:**
> Does gateway setting (**route -n**) still point to your router?

Yes it does. Here is the output:

```
$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.15.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.15.0    0.0.0.0         255.255.255.0   U     0      0        0 eth2
0.0.0.0         192.168.15.1    0.0.0.0         UG    100    0        0 eth2
0.0.0.0         192.168.15.1    0.0.0.0         UG    100    0        0 eth0
```

---

### Post by lensman3 on 2009-10-11
Sounds like the default gateway is not being set correctly. 

The default gateway is found on Linux using the "netstat -r" or "netstat -nr".  "netstat" also works from a XP/Vista/2000 machine in a DOS window.  Go to a windows box and in a DOS box type in "ipconfig".  This should give you the default gateway for one of the working machines.

On your Linux box see if "netstat -nr" shows the default gateway.  One of Two things have gone wrong:

1) The dhcp client on the Linux box is not getting the IP address of the default Gateway.  When it didn't get the Default gateway it also probably didn't get the DNS servers.

2) You are setting up a static IP address on the Linux and didn't fill in the default gateway in the network setup screens.

It also could be a bad DNS..... Can you from a text window ping google.com using the following "ping 74.125.67.100".  The number is one of google's.   If you can ping it, then the Linux machine doesn't have a working DNS.

Hope this helps.

---

### Post by t0mppa on 2009-10-12
> **lensman3 said:**
> Sounds like the default gateway is not being set correctly. 

The default gateway is found on Linux using the "netstat -r" or "netstat -nr".  "netstat" also works from a XP/Vista/2000 machine in a DOS window.  Go to a windows box and in a DOS box type in "ipconfig".  This should give you the default gateway for one of the working machines.

On your Linux box see if "netstat -nr" shows the default gateway.  One of Two things have gone wrong:

1) The dhcp client on the Linux box is not getting the IP address of the default Gateway.  When it didn't get the Default gateway it also probably didn't get the DNS servers.

2) You are setting up a static IP address on the Linux and didn't fill in the default gateway in the network setup screens.

It also could be a bad DNS..... Can you from a text window ping google.com using the following "ping 74.125.67.100".  The number is one of google's.   If you can ping it, then the Linux machine doesn't have a working DNS.

Hope this helps.

In case you didn't realize it from the OP's post above, **route -n** and **netstat -nr** give almost identical outputs (as far as the destination/mask/gateway/interface go anyway). And said post clearly shows that the default gateway is set. Also, it cannot be merely a DNS issue, since OP reported on his first post that ping doesn't work through domain name or IP.

> **brohism said:**
> Yes it does. Here is the output:

```
$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.15.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.15.0    0.0.0.0         255.255.255.0   U     0      0        0 eth2
0.0.0.0         192.168.15.1    0.0.0.0         UG    100    0        0 eth2
0.0.0.0         192.168.15.1    0.0.0.0         UG    100    0        0 eth0
```

Why do you have both eth0 and eth2 active, yet both are connected to the same network and router? I don't see why you'd need two ways to access the same network through the same router.

One definitive problem is that you've two default gateways set up in the main routing table without any rules to tell which one to use and that is disturbing the system as it doesn't know where to send its packets. Kind of like first telling your friend: "Turn left unless I tell you otherwise." and then in the next sentence saying: "Oh, and if I don't say anything, drive straight."

In your case, where both interfaces are connected to the same network through the same router, changing the metrics (routing algorithms use the metrics to calculate the lowest cost route) for routes of one interface might do the trick by getting the system to prefer one interface over the other, but if you really need to use both for some reason, then it gets more complicated.

If you want to have two network interfaces active at the same time, you're going to have to create two routing tables where you configure each interface. And create routes for both interfaces in the main table, referring to their respective tables. After these steps, you add rules telling the system that any traffic coming through interface #1 is routed back through interface #1 and likewise for interface #2, so that interfaces aren't swapped in the middle of the communication.

---

### Post by Iowan on 2009-10-12
[Here]("https://help.ubuntu.com/community/UbuntuBonding") is a link on Bonding - if that's what's up. If not... *never mind*.

---

### Post by brohism on 2009-10-12
> **t0mppa said:**
> In case you didn't realize it from the OP's post above, **route -n** and **netstat -nr** give almost identical outputs (as far as the destination/mask/gateway/interface go anyway). And said post clearly shows that the default gateway is set. Also, it cannot be merely a DNS issue, since OP reported on his first post that ping doesn't work through domain name or IP.



Why do you have both eth0 and eth2 active, yet both are connected to the same network and router? I don't see why you'd need two ways to access the same network through the same router.

One definitive problem is that you've two default gateways set up in the main routing table without any rules to tell which one to use and that is disturbing the system as it doesn't know where to send its packets. Kind of like first telling your friend: "Turn left unless I tell you otherwise." and then in the next sentence saying: "Oh, and if I don't say anything, drive straight."

In your case, where both interfaces are connected to the same network through the same router, changing the metrics (routing algorithms use the metrics to calculate the lowest cost route) for routes of one interface might do the trick by getting the system to prefer one interface over the other, but if you really need to use both for some reason, then it gets more complicated.

If you want to have two network interfaces active at the same time, you're going to have to create two routing tables where you configure each interface. And create routes for both interfaces in the main table, referring to their respective tables. After these steps, you add rules telling the system that any traffic coming through interface #1 is routed back through interface #1 and likewise for interface #2, so that interfaces aren't swapped in the middle of the communication.

Thanks, I'll just set gateway for eth0 since that's my preferred connection.  I have two network cards set up so that one can be used for local network traffic (SMB, etc) while the other can be used to access it remotely (Apache, SSH, etc) since I didn't want the more bandwidth-heavy local traffic to time out the remote traffic.  I'll disable one and see if it works, and get back to you.  Thanks for the help so far!

---

### Post by brohism on 2009-10-12
Ok, I specified only gateway for eth0, and now ping by IP works perfectly fine, but ping by DNS doesn't.  I then disabled eth2, and tried again.  Same result - IP fine, DNS not.  When I ping via domain, it hangs for about 5-8 seconds, then returns a block of 2-3 good ping returns, and then hangs indefinitely.  When I ctrl+C the operation, it hangs for about 10 seconds before giving me a prompt again.  DNS servers are the same as the ones specified on other computers on the network that work flawlessly.

---

### Post by t0mppa on 2009-10-13
> **brohism said:**
> Thanks, I'll just set gateway for eth0 since that's my preferred connection.  I have two network cards set up so that one can be used for local network traffic (SMB, etc) while the other can be used to access it remotely (Apache, SSH, etc) since I didn't want the more bandwidth-heavy local traffic to time out the remote traffic.  I'll disable one and see if it works, and get back to you.  Thanks for the help so far!

Ah, that makes more sense. Although, if the local traffic is bandwidth-heavy enough to push the network to its limits, having another NIC connected to the same network isn't really going to help much. Anyway you should simply set the routing to follow the idea by removing the default gateway from eth2 and the local access from eth0.

> **brohism said:**
> Ok, I specified only gateway for eth0, and now ping by IP works perfectly fine, but ping by DNS doesn't.  I then disabled eth2, and tried again.  Same result - IP fine, DNS not.  When I ping via domain, it hangs for about 5-8 seconds, then returns a block of 2-3 good ping returns, and then hangs indefinitely.  When I ctrl+C the operation, it hangs for about 10 seconds before giving me a prompt again.  DNS servers are the same as the ones specified on other computers on the network that work flawlessly.

That sounds rather odd. A friend has a similar-ish issue, and I haven't found any reasonable fixes for it, so if you find a solution to yours, I'd be interested to see what was wrong.

---

### Post by brohism on 2009-11-19
I'm still trying to figure out how to make this work.  I've removed the second NIC completely, and am only running eth0.  I can access the system fine using the local IP, and if I try to access an Internet location from the server (e.g. ping via SSH) it will work, but it takes a good 5-10 seconds to resolve the host.  Once it does, everything works fine.

Accessing services like Apache and Webmin from outside the local network still isn't working.  Apache starts fine, and I can access it locally without issue.  However, it won't load at all from outside.

It seems to me like there might be a DNS issue on the server.  Any thoughts?

---

### Post by brohism on 2009-12-20
So I'm still fighting with this issue.  I am able to make name-based requests, but it continues to hang for a good 5-10 seconds before resolving, and once it does resolve it seems to take a long time to complete the request.  I'm considering doing a fresh install, but I *really* would like to avoid that, especially since I have a software RAID set up and it would mean backing all the data up, doing the fresh install, and loading it back on since re-creating the RAID would format the drives.

Anybody else find a solution yet?

---

### Post by Iowan on 2009-12-21
After reconfiguration, how does **route -n** look?

---

### Post by brohism on 2009-12-21
> **Iowan said:**
> After reconfiguration, how does **route -n** look?

Which reconfiguration?

---

### Post by Iowan on 2009-12-21
> **brohism said:**
>   I've removed the second NIC completely, and am only running eth0.  This one (sorry for being vague) - running only eth0.

---

### Post by brohism on 2009-12-21
> **Iowan said:**
> This one (sorry for being vague) - running only eth0.

```
$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.15.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.15.1    0.0.0.0         UG    100    0        0 eth0
```

---

### Post by Iowan on 2009-12-21
Rehashing old info, but what is in */etc/resolv.conf*? Is it the same nameserver the other machines use?

---

### Post by brohism on 2009-12-21
> **Iowan said:**
> Rehashing old info, but what is in */etc/resolv.conf*? Is it the same nameserver the other machines use?

Yes, it's using the same servers. It's using OpenDNS.

---

