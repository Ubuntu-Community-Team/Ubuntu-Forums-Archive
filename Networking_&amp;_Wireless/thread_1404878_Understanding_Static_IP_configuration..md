---
title: "Understanding Static IP configuration."
date: 2010-02-11
forum: Networking &amp; Wireless
---

### Post by bkasterm on 2010-02-11
On many places on the internet I have found instructions for configuring a static IP ([http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html](http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html) is one of them).  These instructions have essentially worked for me, although sometimes it seems a little flaky.

I would like to understand better what they do, which parts of the system are affected and in which way.  Any pointers would be appreciated.

Thanks,

Best,
Bart

---

### Post by suseendran.rengabashyam on 2010-02-12
Hi,

The steps mentioned in the link ([http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html](http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html)) would work if you are running an Ubuntu server and additionally you need to mention the DNS servers in /etc/resolv.conf.

If you are running an Ubuntu Desktop, follow these steps:

1) The /etc/network/interfaces file should contain these two lines

```
auto lo
iface lo inet loopback
```

remove all the other entries.

2) Go to System->Preferences->Network Connections->Auto ethX->Edit->IPv4 Settings

3) Change the "Method:" to "Manual" and then click on "Add" to assign the IP address, netmask, gateway, DNS servers, etc.

Please let me know the specific problems that you faced in static IP assignment.

---

### Post by bkasterm on 2010-02-12
Thanks for the refinement of the instructions, that'll certainly help.  What I am looking for at this point is more of an understanding what these changes affect.  Which programs are affected by these changes?  What are the possible parameters?  What should my mental model be of what the machine does with this information?

I.e. the things that would allow me to trouble shoot if it doesn't work.

> **suseendran.rengabashyam said:**
> Hi,

The steps mentioned in the link ([http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html](http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html)) would work if you are running an Ubuntu server and additionally you need to mention the DNS servers in /etc/resolv.conf.

If you are running an Ubuntu Desktop, follow these steps:

1) The /etc/network/interfaces file should contain these two lines

```
auto lo
iface lo inet loopback
```

remove all the other entries.

2) Go to System->Preferences->Network Connections->Auto ethX->Edit->IPv4 Settings

3) Change the "Method:" to "Manual" and then click on "Add" to assign the IP address, netmask, gateway, DNS servers, etc.

Please let me know the specific problems that you faced in static IP assignment.

---

### Post by chili555 on 2010-02-12
All of the programs on your system that depend on internet connectivity just want to know if you have it or not. If you do, they send and receive traffic. If not, they report it to you; ("Firefox cannot find the server at www.example.com"). If you do have connectivity, they use it. They don't care how you got it.

If you are running a server or a networked printer or a media PC, it's obviously easier for other computers to find it if it's address is not always changing. For example, all the computers in my network know that the printer can be found at ipp://192.168.1.117:631/etc. They never have to hunt and miss.

Likewise, if you have traffic coming in from the internet, gaming servers, perhaps, it's easy to set your router to forward that traffic to a single, static IP address.

These kinds of things can be accomplished with DHCP; that is, changing addresses, they are just harder.

From the standpoint of the router, it also doesn't really care, with the exception that static IP addresses need to be assigned outside the DHCP range that the router uses. For example, I set my router to assign DHCP addresses in the range from 192.168.1.100 to x.105. All static addresses have been set at x.106 and higher.

I took an additional step of removing Network Manager on my desktop machines and hard-coding the static details in */etc/network/interfaces*.

---

### Post by bkasterm on 2010-03-08
Following the above instructions or the ones I found on the internet results in not being able to browse the web, and my box not being accessible from the outside.

Which commands can I try to figure out where the error lies?
I.e.
  -- How do I check if my DNS is working/where it is failing?

Thanks.

Best,
Bart

---

### Post by Skaperen on 2010-03-08
DNS can be tested by just trying a simple command line app like "telnet".  Or (learn to) use the "dig" command which can test even more DNS stuff.  For more details, the "tcpdump" command can show DNS queries and replies, but that means learning what those are supposed to be.

You can see what your current running network config is with the command "ifconfig".  It should show the IP address(es) being used.

---

### Post by chili555 on 2010-03-08
If you can do:```
ping -c3 74.125.45.103
```If you get returns, you are connected to the internet. If you do:```
ping -c3 www.google.com
```And you get 'unknown host' then you do not have a correct DNS nameserver. Edit the file */etc/resolv.conf* to add one or more:```
nameserver 192.168.1.1
```You may also use the nameservers in the routers configuration pages or simply use the router's address. Find out with:```
route -n
```Here is an example:> $ route -n
Kernel IP routing table
Destination     [COLOR="Blue"]Gateway [/COLOR]        Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         [COLOR="Blue"]192.168.1.1[/COLOR]   0.0.0.0         UG    0      0        0 eth1

---

### Post by bkasterm on 2010-03-11
> **chili555 said:**
> If you can do:```
ping -c3 74.125.45.103
```If you get returns, you are connected to the internet. If you do:```
ping -c3 www.google.com
```And you get 'unknown host' then you do not have a correct DNS nameserver. Edit the file */etc/resolv.conf* to add one or more:```
nameserver 192.168.1.1
```You may also use the nameservers in the routers configuration pages or simply use the router's address. Find out with:```
route -n
```Here is an example:

ping -c3 74.125.45.103

Gives me Destination Host Unreachable

ping -c3 [www.google.com](www.google.com)

Gives me "unknown host www.google.com"

The contends of /etc/resolv.conf show exactly the nameservers that my laptop (plugged in via a switch on the same plug in the wall) is using; that is the one where I am composing this message (and so is clearly working).

---

### Post by bkasterm on 2010-03-11
I have one possible hint for what might be happening:

This the the result when I try to have my static ip active

```

kasterma@boef2:/etc$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
128.138.150.1   0.0.0.0         255.255.255.255 UH    0      0        0 eth0
128.138.146.0   0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         128.138.150.1   0.0.0.0         UG    0      0        0 eth0

```

This is the result when I am through DHCP

```

kasterma@boef2:/etc$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
128.138.150.0   0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         128.138.150.1   0.0.0.0         UG    0      0        0 eth0

```

The first line is different.  Of course I do not understand any of the lines, so it is not helping me much.  But I hope someone reading this can tell me what it means.

Thanks.

Best,
Bart

---

### Post by NiGhtMarEs0nWax on 2010-03-16
you are not connected to your gateway.

---

### Post by oldfred on 2010-03-16
These are my entries. I orginally tried to use the same number that the DHCP was assigning but the router does not accept that, it must be outside the DHCP range used by the router.

---

### Post by bkasterm on 2010-03-17
> **NiGhtMarEs0nWax said:**
> you are not connected to your gateway.

How can you tell?

BTW: I am traveling now, I'll not return to this computer until next week (and as long as the static ip is not set up I obviously can't reach it from the outside).

---

### Post by bkasterm on 2010-03-28
After reinstalling ubuntu 9.10 (so I know I have a clean slate) I now get the outputs as follows (the first one is with the settings for my static ip, the second one through DHCP).  I think now I am connected to the gateway, but still not to the internet.

```

kasterma@boef2:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
128.138.146.0   0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         128.138.146.1   0.0.0.0         UG    0      0        0 eth0
kasterma@boef2:~$ ping www.google.com
ping: unknown host www.google.com
kasterma@boef2:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
128.138.150.0   0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         128.138.150.1   0.0.0.0         UG    0      0        0 eth0
kasterma@boef2:~$

```

---

### Post by chili555 on 2010-03-28
It appears that something is amiss in your configuration. Did you make these settings in Network Manager or /etc/network/interfaces? Please post your /etc/network/interfaces. 

Do you know the IP address of your router/modem/switch; from another computer, for example?

---

### Post by bkasterm on 2010-03-28
I made the settings using Network Manager.  The following picture shows them set.

[IMG]http://bartk.nl/Settings.png[/IMG]

I do not know which address you think I should know about that is not shown  here.  It is not on a homenetwork, it is at my department.

---

### Post by chili555 on 2010-03-28
Are you the only computer in the department? On one of the others, a Windows computer, for example, is the gateway address 128.138.[COLOR="Blue"]146[/COLOR].1?

I wonder where this is coming from.> $ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
128.138.150.0   0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         128.138.[COLOR="Blue"]150[/COLOR].1   0.0.0.0         UG    0      0        0 eth0


---

### Post by bkasterm on 2010-03-29
> **chili555 said:**
> Are you the only computer in the department? On one of the others, a Windows computer, for example, is the gateway address 128.138.[COLOR="Blue"]146[/COLOR].1?

I wonder where this is coming from.

Thanks!

It seems that in my IP application I filled out the wrong building number.  I have send the network administrator an email correcting this information, and hope to get corrected numbers soon.  I'll let you know if this fixes things.

---

### Post by bkasterm on 2010-03-29
All working now; Thanks for the help.

In the end (now that I have the right numbers) the instructions by suseendran.rengabashyam worked.  Also in solving this I have made some minor progres in actually understanding what is going on; that is I have better understanding of what the numbers mean (but certainly not very good yet).

Also that in the end chili555 needed to observe something wrong with my numbers, as opposed to "command so and so shows there is something wrong" feels a little unfortunate.

---

### Post by chili555 on 2010-03-29
We've all been there and done that! If we were all perfect, there wouldn't need to be a forum. We're all here to help each other and I hope you can help others and maybe me in the future.

---

