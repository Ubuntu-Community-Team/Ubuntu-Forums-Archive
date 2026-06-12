---
title: "Server problem with setting a static IP Address"
date: 2009-12-02
forum: Networking &amp; Wireless
---

### Post by TheDelChop on 2009-12-02
Guys,

I've got a question about setting my ip address on my server to be static.

I've basically done the following:

I've edited my /etc/network/interfaces file so it looks like the following:

```

xample static IP setup: (broadcast and gateway are optional)
     #
     auto eth0
     iface eth0 inet static
          address 192.168.0.11
          netmask 255.255.255.0
          gateway 192.168.0.1

```

My resolv.conf file contains my nameservers, and my /etc/hostname files contains the name of my server.

I then restarted my networking by running /etc/init.d/networking restart.

This seems to work corretly.  My IP Address is assigned to the address I specified.  However, after rebooting my server, my IP address was reassigned by the DHCP server.  

I have read in some various places that I need to remove the definition of my name servers in /etc/resolve.conf to stop this.  

Anybody have any ideas where I"m going wrong?

---

### Post by chili555 on 2009-12-02
> However, after rebooting my server, my IP address was reassigned by the DHCP server. What does dmesg report after this happens?```
dmesg | grep eth0
```May we safely assume that Network Manager, Wicd and other similar nasties have been removed?

---

### Post by TheDelChop on 2009-12-02
```
[    2.830996] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x3f1 @ 1, addr 00:50:8d:d3:c9:3c
[   15.590029] eth0: no IPv6 routers present
[  620.610017] eth0: no IPv6 routers present
[  989.640016] eth0: no IPv6 routers present

```

This is the output of that commnad.  Yes, I installed Ubuntu 9.10 Server so I'm assuming that network manager etc have been removed.

Joe

---

### Post by chili555 on 2009-12-02
May we please see:```
cat /etc/resolv.conf
cat /etc/hosts
```Thanks.

---

### Post by TheDelChop on 2009-12-02
Contents of /etc/resolv.conf
```

nameserver 68.105.28.12
nameserver 68.105.29.12
nameserver 68.105.28.11

```

Contents of /etc/hosts

```

127.0.0.1       localhost.localdomain                   localhost
192.168.0.105    server.synantus.com                    synantus

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by chili555 on 2009-12-02
Ahh! My favorite kind of problem: everything looks great but it just doesn't work right! Please do:```
dmesg > dmesg.txt
```Attach the text file to your reply. Please do not flood the forum by posting dmesg in the body of your post. Thanks.

---

### Post by TheDelChop on 2009-12-02
Ok here you go. I zipped it up since the forum complained about the size. Thanks again.

Joe

---

### Post by TheDelChop on 2009-12-02
Chili, strangely after a reboot it appears as if this works just fine now.  I'm sorry if I wasted any of your time, but thank you for your help.

Joe

---

### Post by chili555 on 2009-12-02
Happy to help. I'm glad it's working for you!

---

