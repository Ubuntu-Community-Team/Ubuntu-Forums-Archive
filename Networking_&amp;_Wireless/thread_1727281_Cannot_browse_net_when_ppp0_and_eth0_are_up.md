---
title: "Cannot browse net when ppp0 and eth0 are up"
date: 2011-04-12
forum: Networking &amp; Wireless
---

### Post by slashwannabe94 on 2011-04-12
Hello all, 

I'm a n00b with these things so be nice please XD

I have recently touched on this in previous posts but never came to actually trying to fix it. I have a D-Link DSL-2640R router, with dhcp disabled. It is connected to my computer via ethernet. I have the network manager configuration set to manual with an address of 192.168.1.2, Mask 255.255.255.0 and the gateway column is blank. I would like to know why my eth0 interface seems to stop me browsing. 

I use a T-Mobile HUAWEI usb mobile broadband stick, Model E1750 for internet access. 

If anyone has any ideas as to why this is happening please discuss them. 

I have also tried editing the /etc/sysctl.conf file and uncommented the 
[COLOR=Blue]net.ipv4.ip_forward=1[/COLOR]
line to enable ipv4 packet forwarding. This has not solved my problem. 

Thanks, 

SlashWannabe94

---

### Post by SeijiSensei on 2011-04-12
Make sure your default gateway points to the other end of your PPP connection.  Use the command "route -n" and look at the final line that begins with 0.0.0.0.  What does it have under Gateway?  Is the other end of the PPP connection or some address in the network connected to eth0?

Please post the results of "route -n" and the contents of /etc/network/interfaces.  Put the text in [noparse][code][/noparse] tags.

---

### Post by slashwannabe94 on 2011-04-12
this is with both interfaces connected. 

route -n 

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.64.64.64     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ppp0
0.0.0.0         10.64.64.64     0.0.0.0         UG    0      0        0 ppp0

```

/etc/network/interfaces
```

auto lo
iface lo inet loopback

```

Thanks, 
SlashWannabe94

---

### Post by SeijiSensei on 2011-04-12
If 10.64.64.64 is also the default gateway without the ethernet interface enabled, I don't know what the problem might be.

10.64.64.64 is the *remote* end of the PPP connection, yes?  If you run "ifconfig -a" you'll see an entry for ppp0 that should display both the local and remote IP address.

---

### Post by slashwannabe94 on 2011-04-12
This is true dude. With both interfaces connected the code i give you is what i still get. I am having no luck with this.

---

