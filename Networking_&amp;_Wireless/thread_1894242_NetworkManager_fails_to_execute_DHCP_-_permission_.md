---
title: "NetworkManager fails to execute DHCP - permission denied to dhclient by apparmor"
date: 2011-12-12
forum: Networking &amp; Wireless
---

### Post by robajz on 2011-12-12
I have installed 32bit Oneiric kubuntu (11.10) on eee pc 901. As usual, I moved the /usr directory to the second disk, becuse the primry root disk only has 4GB and would not fit all my apps and caches etc... The move I make with a symbolic link. My /usr is in the /home and I linked it: ln -s /home/usr /usr

Now here is the problem I presume. Apparmor denies access to dhclient because the apps are not in /usr/lib/ but rather /home/usr/lib since /usr => /home/usr

When I try to connect the wired eth1 interface with kde network manager, it stays hanging for a while in "setting network address" and then does not connect. In the meantime, syslog sees entries of permission denied from apparmor.

However, "sudo dhclient eth1" works perfectly (if not interfered with by NM).

I feel the solution is not to link /usr to /home/usr but rather make a propper mount. I don't like that though because that would fix-slice the space on the 16GB secondary drive and it is already tight ;) symlinking gives more flexibility. Also, this setup worked for me in Natty and is broken in Oneiric so something must have changed...

Also I feel this is an interesting topic for a debate. Should NM fail in such a situation and should it fail this way (no indication to the UI of the root cause)?

I tried to **fix the apparmor profile for dhclient** but I failed. I'll need some help with that if you can please ;) Or is it just plain silly idea?

Syslog for reference $ sudo tail -f /var/log/syslog | grep NetworkManager
```

Dec 12 11:02:07 112358 NetworkManager[691]: <info> Activation (eth1) starting connection 'Wire'
Dec 12 11:02:07 112358 NetworkManager[691]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Dec 12 11:02:07 112358 NetworkManager[691]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Dec 12 11:02:07 112358 NetworkManager[691]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Dec 12 11:02:07 112358 NetworkManager[691]: <warn> (eth1): failed to change interface MAC address
Dec 12 11:02:07 112358 NetworkManager[691]: <warn> (eth1): failed to set MAC address to 93:1F:53:DB:43:64
Dec 12 11:02:07 112358 NetworkManager[691]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Dec 12 11:02:07 112358 NetworkManager[691]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Dec 12 11:02:07 112358 NetworkManager[691]: <info> (eth1): carrier now OFF (device state 40, deferring action for 4 seconds)
Dec 12 11:02:07 112358 NetworkManager[691]: <info> (eth1): carrier now ON (device state 40)
Dec 12 11:02:07 112358 NetworkManager[691]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Dec 12 11:02:07 112358 NetworkManager[691]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Dec 12 11:02:07 112358 NetworkManager[691]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) successful.
Dec 12 11:02:07 112358 NetworkManager[691]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Dec 12 11:02:07 112358 NetworkManager[691]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Dec 12 11:02:07 112358 NetworkManager[691]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Dec 12 11:02:08 112358 NetworkManager[691]: <info> (eth1): device state change: config -> ip-config (reason 'none') [50 70 0]
Dec 12 11:02:08 112358 NetworkManager[691]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Dec 12 11:02:08 112358 NetworkManager[691]: <info> dhclient started with pid 11175
Dec 12 11:02:08 112358 NetworkManager[691]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Dec 12 11:02:08 112358 dhclient: execve (/usr/lib/NetworkManager/nm-dhcp-client.action, ...): Permission denied
Dec 12 11:02:08 112358 kernel: [ 4458.877970] type=1400 audit(1323680528.023:103): apparmor="DENIED" operation="exec" parent=11175 profile="/sbin/dhclient" name="/home/usr/lib/NetworkManager/nm-dhcp-client.action" pid=11176 comm="dhclient" requested_mask="x" denied_mask="x" fsuid=0 ouid=0
Dec 12 11:02:08 112358 dhclient: execve (/usr/lib/NetworkManager/nm-dhcp-client.action, ...): Permission denied
Dec 12 11:02:08 112358 kernel: [ 4458.897573] type=1400 audit(1323680528.043:104): apparmor="DENIED" operation="exec" parent=11175 profile="/sbin/dhclient" name="/home/usr/lib/NetworkManager/nm-dhcp-client.action" pid=11177 comm="dhclient" requested_mask="x" denied_mask="x" fsuid=0 ouid=0

```

---

### Post by robajz on 2011-12-12
> **robajz said:**
> 
I tried to **fix the apparmor profile for dhclient** but I failed. I'll need some help with that if you can please ;) Or is it just plain silly idea?


Oh Glory! A hint in [another ubuntu forums archive]("http://ubuntuforums.org/archive/index.php/t-1496700.html") got me there!

$ sudo nano /etc/apparmor.d/tunables/alias
```

alias /usr/ -> /home/usr/,

```

$ sudo service apparmor reload

And it worked! NM can now connect without any trouble. It did not work for deepesh though for some reason...

Lesson: When you symlink /usr, make an alias for it in apparmor!

---

