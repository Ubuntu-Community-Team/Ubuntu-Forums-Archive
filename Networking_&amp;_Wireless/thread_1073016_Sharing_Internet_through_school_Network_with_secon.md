---
title: "Sharing Internet through school Network with second Ethernet Port"
date: 2009-02-17
forum: Networking &amp; Wireless
---

### Post by montgoja on 2009-02-17
I have no idea honestly if a question like this has been posted before, but my apologies for reposting if it has.

I am connected to my college wired network on my main desktop computer.  Now, my computer has two ethernet ports on the mobo and I would like to be able to share the internet connection through my main computer and into my laptop (via another ethernet cable), which is currently running Windows XP SP3.  I tried to follow the instructions from [http://ubuntuforums.org/showthread.php?t=713874](http://ubuntuforums.org/showthread.php?t=713874) but it appears to be discussing the use of a router, which I do not have.

If this is even possible to do, could someone please post some step-by-step instructions?  I'm comfortable with using the terminal and changing settings, as long as I know exactly what to do and how to fix things if I totally blow my network connections up.  I'm simply looking for a relatively uncomplicated way to go Internet -(ethernet)-> Main Computer -(second ethernet port and cable)-> Laptop.

Thanks!

---

### Post by dmizer on 2009-02-17
You'll need a [crossover cable](http://en.wikipedia.org/wiki/Ethernet_crossover_cable). Then you can make use of that howto without a router.

---

### Post by montgoja on 2009-02-18
Thanks!  I'll have to pick one up!

Another couple questions:

1) Will making my computer's IP adress into a static IP have any possibilities of running into issues with my school's network?

2) In the howto, it tells me to look for the line: #net.ipv4.conf.default.forwarding=1
and remove the comment.  When I search through the .conf file for that line, it is nonexistent.  should I simply insert this line?  I'm assuming yes, but want to double check.

3) Considering my concerns in question 1, would it be better to set up the static IP address or to use the dhcp server option?

Thanks again for the help!

---

### Post by dmizer on 2009-02-18
You have two network cards in your main computer. Each of these cards represents a side to your network. For example:

School side
LAN side

Where "School side" is the network card connected to your school network, and "LAN side" is the network card you will be connecting your laptop to. 

You should not touch the school side of the network. If it's not currently static IP, don't change it. The only thing you need to manipulate is the LAN side of the network. It won't matter to your school side if your LAN side is static or not.

I suggest that you start by configuring your LAN side as static rather than trying to configure a DHCP server, as a DHCP server adds complexity. If you get things working with a static IP, you can think about adding a DHCP server later.

As to your edit question, which version of Ubuntu are you using on your main computer?

---

### Post by montgoja on 2009-02-18
I believe I'm using Hardy (8.04), as it's the last full distro upgrade I recall performing.

---

### Post by dmizer on 2009-02-18
Actually, you'll need to add two lines to /etc/sysctl.conf:
```
net.ipv4.conf.default.forwarding=1
net.ipv4.conf.all.forwarding=1
```
If they're not there, just add them.

---

### Post by montgoja on 2009-02-19
Another question:
I just found this section of code in the sysctl.conf file (sorry I don't know how to make the code box):

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1

# Uncomment the next line to enable packet forwarding for IPv6
#net.ipv6.ip_forward=1

Is this what the howto was telling me to uncomment?  Or do I leave that alone and just add in the two lines you said above?

---

### Post by dmizer on 2009-02-19
Humm, I'll have to look into this more later. Looks like the syntax may have changed slightly.

At this point, it will be easier for you to just add the two lines at the end of the file, that way it's easy to see where you've made the edit, and if it doesn't work you can remove them.

If you use the advanced edit, there is an icon to add code tags, otherwise you can manually enter the tag like so: [noparse]```
terminal output here
```[/noparse]

---

### Post by montgoja on 2009-02-19
Ok... picked up a crossover cable and tried step by step last night.  I have the static IP set, made the edits it said to make, but my laptop is showing only "Limited or no connectivity" with no internet access.  In addition, the changes seem to have possibly affected my Azureus connection, but I'm not saying anything for certain there because the school network has always been shoddy for torrenting.

The crossover cable I picked up is RJ45 male/male, according to Staples' packaging.

What do I need to post to troubleshoot?

Thanks again

---

### Post by dmizer on 2009-02-19
Please post the output of:
```
ifconfig
```

---

### Post by montgoja on 2009-02-20
```
 eth0      Link encap:Ethernet  HWaddr 00:17:31:8f:d2:46  
          inet addr:10.8.16.1  Bcast:10.8.16.0  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

eth1      Link encap:Ethernet  HWaddr 00:17:31:8f:dc:bb  
          inet addr:10.38.9.43  Bcast:10.38.255.255  Mask:255.255.0.0
          inet6 addr: fe80::217:31ff:fe8f:dcbb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4433 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4197 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1769066 (1.6 MB)  TX bytes:734933 (717.7 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1667 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1667 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:83820 (81.8 KB)  TX bytes:83820 (81.8 KB)

wlan1     Link encap:Ethernet  HWaddr 00:15:af:04:c0:99  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:42 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

---

### Post by dmizer on 2009-02-20
Humm, that looks right. What IP did you set the XP laptop to?

Also, please post the output of:
```
sudo iptables -L
```

It may also help if you disable IPv6: [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

---

### Post by montgoja on 2009-02-23
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination     

```

As to the IP address of the XP laptop, I have assigned it to 10.8.16.8, subnet mask 255.255.255.0, gateway 10.8.16.1 and the DNS server from my resolv.conf file.

It looks like I just forgot to assign the XP laptop an IP address.  Thanks for all the help!  I'm fully connected now!

Any ideas on fixing my NAT issues for Azureus?  Since making the changes addressed in the HowTo, I'm consistently getting a "NAT OK?" message from the program.  Beforehand, I wasn't getting a great deal of speed anyway, but now it's been practically cut down to Bytes/second.

Thanks again!

---

### Post by dmizer on 2009-02-23
Honestly, you'll have more luck with a different client. You may be sucessful with Azureus if you install Sun Java and [force it](https://help.ubuntu.com/community/Java) to use the non-free Java instead of the open source version.

Transmission comes with Ubuntu by default, and is a very excelent torrent client, try that and see if you get better results. This will tell you if the problem is in your system configuration or if the problem is with Azureus.

---

### Post by montgoja on 2009-02-23
Thanks for the tip on Transmission!  I'm getting closer to 150 KB/s with this on a couple torrents.  None of the ports are open, of course, so I can only wonder what blazing speed I'd have with an open campus connection!

---

