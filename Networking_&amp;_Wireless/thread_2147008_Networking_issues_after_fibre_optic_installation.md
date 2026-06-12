---
title: "Networking issues after fibre optic installation"
date: 2013-05-20
forum: Networking &amp; Wireless
---

### Post by AmbiguousOutlier on 2013-05-20
Hi there, I've recently got fibre optic installed and some things are not working as they did when I had ADSL a few hours earlier. Specifically with my server, I must have done something a few days or weeks ago and I decided to reboot the server to see if that resolved the issues I am having. All this did was change my IP from Static back to DHCP and caused a few other problems. 

When I reconfigure /etc/network/interfaces back to static, My NFS shares are all working, however SSH doesn't work. Ping'ing the server gets 100% packet loss although I can ping out of the server fine. 
 
```

auto eth0
iface eth0 inet static
        address 192.168.1.100
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1

```

```

sudo /etc/init.d/networking restart

```
(it did say this was deprecated however I overlooked this as it did correctly assign my private IP)


If I can figure out how to ping my server, I'm sure ssh will start working. 

Can anyone point me in the right direction please?

---

