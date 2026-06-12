---
title: "Unable to configure ethernet with network configuration"
date: 2011-04-18
forum: Networking &amp; Wireless
---

### Post by iankellogg on 2011-04-18
I am using Ubuntu 10.10 32 bit. I need to use a static IP address with the network in order to get online but the Network Configuration applet will only show "auto ethernet". I have a profile in the "edit connections" but I can only see "Auto Ethernet". If I select "auto Ethernet" it creates a new profile by the same name. If i disconnect and reconnect to "auto Ethernet" it creates another profile. 

I am able to get online with /etc/network/interfaces and /etc/init.d/networking restart but this is quite annoying since I have to do it every time I start and applications often think there is no internet connection and refuse to run. 

Is there something I am missing?

---

### Post by Iowan on 2011-04-18
The "auto ethernet" *should* still allow you to configure it for a static address. It *should* also allow you to disable the "connect automatically" option - which might(?) make another profile work better.

---

### Post by iankellogg on 2011-04-19
If I modify the auto ethernet profile at all when I try to connect, it just creates another auto ethernet profile so that I am now left with two auto ethernet profiles. I have multiple profiles that are set correctly but the only profile that I can select from the nm-applet is auto ethernet.

I am using a brand new fresh install as well. It will not show me any of the profiles I have created.

---

### Post by dineshs on 2011-04-20
First let your /etc/network/interfaces read only
auto lo
iface lo inet loopback
Restart and configure your connection as explained [here]("http://ubuntuforums.org/showpost.php?p=9467538&postcount=5")

---

### Post by iankellogg on 2011-04-20
[[IMG]http://i.imgur.com/XZsDN.jpg[/IMG]](http://imgur.com/XZsDN)

This is what I see. The profile I created does not show up in the available networks and auto ethernet is the only thing I see. If I select auto ethernet it makes a profile by the same name. If I edit that new "auto ethernet" profile and try to connect to it, it creates a new "auto ethernet" profile.

---

### Post by dineshs on 2011-04-21
Please post the results of```
ls /etc/NetworkManager/system-connections
```and```
cat /etc/network/interfaces
```

---

### Post by theprofessor102 on 2011-04-21
> **iankellogg said:**
> I am using Ubuntu 10.10 32 bit. I need to use a static IP address with the network in order to get online but the Network Configuration applet will only show "auto ethernet". I have a profile in the "edit connections" but I can only see "Auto Ethernet". If I select "auto Ethernet" it creates a new profile by the same name. If i disconnect and reconnect to "auto Ethernet" it creates another profile. 

I am able to get online with /etc/network/interfaces and /etc/init.d/networking restart but this is quite annoying since I have to do it every time I start and applications often think there is no internet connection and refuse to run. 

Is there something I am missing?

In /etc/network is a file interfaces
my file is
/etc/network/interfaces
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
# auto eth0
# iface eth0 inet dhcp
auto eth0
iface eth0 inet static
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.1

```

Hope this helps.

---

