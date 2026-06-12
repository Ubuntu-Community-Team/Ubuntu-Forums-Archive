---
title: "Connecting"
date: 2009-04-10
forum: Networking &amp; Wireless
---

### Post by ufarmer on 2009-04-10
I have Ubuntu 8.10 running on my laptop.  The network manager detects my wireless modem, authenticates, and then claims to have a connection.  However I am unable to connect to the internet.

Strangely, if I just plug the laptop into one of the spare ports on the router using an ethernet cable, sometimes it can connect to the internet and sometimes it cannot.  Rebooting has no effect on this.

I tried sudo apt-get install linux-backports-modules-intrepid-generic

but nothing has changed.

Any advice is appreciated.

---

### Post by Paranoid Tux on 2009-04-10
What is the content of your /etc/resolv.conf file, the output of your ifconfig command, and does your wireless modem use dhcp?

---

### Post by ufarmer on 2009-04-11
Hi.

/etc/resolv.conf is empty.

The output of ifconfig is :

eth0      Link encap:Ethernet  HWaddr 00:1c:25:a0:53:b9  
          inet6 addr: fe80::21c:25ff:fea0:53b9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:60 (60.0 B)  TX bytes:468 (468.0 B)
          Memory:fc200000-fc220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:968 (968.0 B)  TX bytes:968 (968.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:21:6b:ca:8e:5c  
          inet6 addr: fe80::221:6bff:feca:8e5c/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:498 (498.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-21-6B-CA-8E-5C-65-35-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

I have a wired/wireless router that is connected to my modem.  My desktop computer is connected by an ethernet cable into one of the ports on the router and is able to connect no problem.  Ubuntu on my laptop detects the wireless network and claims to be connected but I can't actually access the internet.  And when I connect the laptop by an ethernet cable to one of the ports on my router -- which is already connected to the internet -- it can't detect/use the connection.

Thanks for the help.

---

### Post by Paranoid Tux on 2009-04-11
You do not have dhcp enabled. Set your router/switch to enable dhcp and then reboot everything. See if that makes it any easier.

Cheers,

Paranoid

---

### Post by ufarmer on 2009-04-12
The setting named "DHCP Server" is enabled.

I got the wireless connection on the laptop working by installing ndiswrapper.  I would still like to be able to plug the laptop into the router directly for times when I want a faster connection.  I ran "lshw" and it says my "Ethernet interface" is disabled.  Is that the problem?  And, if so, how do I enable it?

---

### Post by Paranoid Tux on 2009-04-12
Enable your ethernet interface by typing

```
sudo ifconfig eth0 up
```

That should fix that. Let me know how you go.

---

### Post by ufarmer on 2009-04-12
"sudo ifconfig eth0 up" did not work.  I checked "lshw" again and noticed that the "Ethernet interface" was called "pan0" so I tried "sudo ifconfig pan0 up" also with no luck.

---

### Post by Paranoid Tux on 2009-04-12
I am sorry then, I would suggest that you google the problem for your specific hardware and distro that you are using. You have an eth0 interface and despite what else it might be called, thsi should work. Sometimes in Gnome and KDE there are netwrk management programs that overrule that action though, so check into that too.

Sorry that I couldn't be of more help.

Good luck,

Paranoid

---

### Post by ufarmer on 2009-04-12
Thanks, Paranoid.

---

