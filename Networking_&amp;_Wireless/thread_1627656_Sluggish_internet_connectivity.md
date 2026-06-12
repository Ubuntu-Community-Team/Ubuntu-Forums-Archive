---
title: "Sluggish internet connectivity"
date: 2010-11-21
forum: Networking &amp; Wireless
---

### Post by Vanish00 on 2010-11-21
I'm using Ubuntu 10.10 32-bit desktop version and connecting to the Internet by a wire connection. I use firefox as my main browser but tried other browsers as well but they all seem to load whenever they want. I've read other threads which suggested disabling IPv6 which I did for firebox browser and for the system.

Problem: I find myself constantly refreshing a page just to load up and if it doesn't it just hangs at "waiting...." OR "transfering...". Similarly, youtube videos tend to just stop loading half-way through, or my internet radio stream just stops till I refresh it again. I want to stick with Ubuntu but when I switch back to windows this is a non-issue. 

Any sugguestions/fixes?

---

### Post by Vanish00 on 2010-11-21
Anybody else with a similar problem? I'm thinking about getting a wireless card because I've read around and found that this issue is with a wire connection only.

---

### Post by TracyO on 2010-11-21
My problem is that not all internet sites load.  Since I upgraded to 9.10 and then 10.04, sites with video like YouTube or where I have to log in don't work very well.  It's universal with all browsers but doesn't seem to be related to my connection.  However, the error notice that I get is that the internet connection was reset.

Do your pages eventually load?

---

### Post by uncaspi on 2010-11-21
Which driver do you have for the card? sudo lshw -C network

---

### Post by Vanish00 on 2010-11-21
This is the result I get from the command: sudo lshw -C network

```

  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 01
       serial: 00:1a:92:74:bf:64
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.15.7 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:44 ioport:a800(size=256) memory:feaff000-feafffff memory:feac0000-feadffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```

---

### Post by Vanish00 on 2010-11-21
> **TracyO said:**
> My problem is that not all internet sites load.  Since I upgraded to 9.10 and then 10.04, sites with video like YouTube or where I have to log in don't work very well.  It's universal with all browsers but doesn't seem to be related to my connection.  However, the error notice that I get is that the internet connection was reset.

Do your pages eventually load?

My pages kinda load eventually.  What I mean is usually on first load to the site just a blank page and continually processing but nothing.  I have to stop and refresh then I actually get the content.  Once I get the content it appears I have the whole page loaded but browser still appears to be processing so I always have to stop the page.

---

### Post by dineshs on 2010-11-22
I think you need to check MTU, DNS or ipv6(which you have already disabled)
Are you using network manager ?If yes rightclick NM icon and edit the wired connection to set a different DNS (say [COLOR="Blue"]4.2.2.1 or 8.8.8.8[/COLOR])or different MTU say 1492 or 1482).
Regarding MTU [here]("http://ubuntuforums.org/showthread.php?t=872346") is a link which explains how you can findout the optimum MTU value)
Note :You may have to restart the machine for the changes to take effect
or run ```
sudo service network-manager restart
```

---

### Post by Vanish00 on 2010-11-22
I don't know where network manager is but no I am not using it.  I've been using network connections and the only place I see anything mention DNS is in the IPv4 Settings.  Under that tab my method is set to "Automatic(DHCP)" and the DNS servers are greyed out but with no address in them.  I did adjust the MTU but problem still remains.

So at this point I think the issue is with DNS but not knowledge in how to handle DNS or where to beginning on adjusting that.  I might need a little more detail when it comes to this, if you have to explain a possible fix.  Appreciate the help so far!

---

### Post by uncaspi on 2010-11-22
You may have a look at this thread before you do anything else.

[http://ubuntuforums.org/showthread.php?t=1626912](http://ubuntuforums.org/showthread.php?t=1626912)

---

### Post by Vanish00 on 2010-11-24
Thanks for the info on your link but most of the address wireless connection which I am using a wire connection to my desktop.  I did try to apply that information to my case but I still have to refresh constantly on random websites just to get most of the content to load and even then it's not completely transferred.

When I ping ubuntu.com:

--- ubuntu.com ping statistics ---
112 packets transmitted, 64 received, 42% packet loss, time 267137ms
rtt min/avg/max/mdev = 156.277/162.300/180.583/5.593 ms


Any other advice out there?

---

### Post by Vanish00 on 2010-11-24
I resolved my issue by the link below by getting "wicd".  Thanks all who tried to help me!

[http://superuser.com/questions/70544/what-could-cause-a-huge-packet-loss-in-ubuntu-9-10-for-both-wired-and-wireless]("http://superuser.com/questions/70544/what-could-cause-a-huge-packet-loss-in-ubuntu-9-10-for-both-wired-and-wireless")

---

