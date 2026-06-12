---
title: "Static IP giving loads of grief"
date: 2009-10-27
forum: Networking &amp; Wireless
---

### Post by noblerabbit on 2009-10-27
Hello everyone,

I recently started running my home computer as a server for simple web pages I am working on, and one of the things required is a static IP from the router, to save me changing the traffic forwarding each time I start my computer and get a new IP.

This has caused all kinds of problems. 

What I did was to add this to /etc/network/interfaces :
```

auto lo
iface lo inet loopback

#mapping hotplug
#
#    script grep
#    map eth0
#auto eth0
#iface eth0 inet static
#    address 192.168.1.22
#    netmask 255.255.255.0
#    network 192.168.1.0
#    broadcast 192.168.1.255
#    gateway 192.168.1.1
#

```..commented out as you can see, because it is failing hard.

I originally added that stuff (with 22 being mine, as it is unlikely to conflict with the router assigning IPs to other devices in the house) 
and did a /etc/init.d/networking restart

It worked initially, but upon restarting the machine I have no access to internet. I can get to the router but no further. Even commenting out (as above) and restarting networking, and even restarting the machine, still my IP (in network manager) says I am .22 and it also wont let me on. I can change the interfaces file to other stuff, like .12 and that is recongised byu network manager, but still I cannot get online.

You may be wondering how I can post this, well my mobo has built in wireless so I got on that instead, which seems to work just fine, since it is not listed in the interfaces file.

I really dont get whats going on here...:(:(

---

### Post by noblerabbit on 2009-10-27
Ugh OK update:

Just for experimentation I did

sudo ifconfig eth0 down

then 

sudo ifconfig wlan0 down

Then

sudo ifconfig eth0 up

And now eth0 is working again, giving me internet....

I am still on .22 but have got the interfaces stuff commented out, as above in first post...

---

### Post by Iowan on 2009-10-27
DNS must be manually set when using static address - and sometimes it gets overwritten.  See if your router (DHCP server) can issue a static *lease* based on MAC address. Your machine will always get the same address, but reap the other benefits of a DHCP address. Otherwise, check contents of */etc/resolv.conf* to see if the proper nameservers are there. You can also try to **ping** names and addresses to see if addresses work, but names fail (another clue to DNS issues).

---

