---
title: "Wired Network enabled, still doesn't load pages"
date: 2012-03-18
forum: Networking &amp; Wireless
---

### Post by Siilis on 2012-03-18
I use a wired network to switch between my Linux laptop and Windows PC. Now the laptop can't load any pages, but it shows that Wired Network connected. It works fine on the Windows PC. I checked the IP, DNS, Gateways e.c. and they are the same on both machines. Also, in System Manager, it shows that there is a internet connection. The page is loaded for lie 10 seconds, then a "no connection established" error shows up. I also tried pinging some sites, but it showed that the website adress was put in wrong, I tried [http://google.com](http://google.com) but it didn't work. Any ideas on how to fix this?

---

### Post by ajgreeny on 2012-03-18
Try ```
ping -c 5 www.google.com
```

---

### Post by Siilis on 2012-03-18
Tried that, it says:
ping: unknown host [www.google.com](www.google.com)

---

### Post by matt_symes on 2012-03-18
Hi

Try 

```
ping -c 5 8.8.8.8
```

If the above command succeeds (it's one of Google's nameservers) whereas the other one failed then i would say it's a problem with you DNS settings.

If the above command succeeds then try

```
nslookup www.google.com
```

Post back the output.

Kind regards

---

### Post by winh8r on 2012-03-18
retracted

---

### Post by Siilis on 2012-03-18
Ok, tried pinging. It says:

---8.8.8.8 ping statistics ---
5 packets transmitted, 0 received, 100% packets loss, time 4032ms

I tried the nslookup [www.google.com](www.google.com) command too.

;; connection timed out; no servers could be reached

---

### Post by matt_symes on 2012-03-18
Hi

It's not DNS then. It's your connection somewhere or drivers on your PC.

Can you ping your router ? Try doing that.

```
ping -c 3 <router_ip>
```

Open a terminal and type

```
sudo lshw -c network
```

Post that back here.

Do you have an IP address ? You can check with this command.

```
ifconfig eth0
```

This command below will show if you are physically connected to your router. It will highlight broken cables (etc)

```
cat /sys/class/net/eth0/carrier
```

You are looking for a 1 to be displayed and not a 0 like this.

```
matthew@matthew-Aspire-7540:~$ cat /sys/class/net/eth0/carrier 
1
matthew@matthew-Aspire-7540:~$
```

A 1 means you are physically connected to the router.

I am assuming your device is called eth0. You will need to change it if it is not the case.

Kind regards

---

### Post by Siilis on 2012-03-18
Tried everything but sadly I don't know my router IP.
ligita@ligita-laptop:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:1d:72:2c:9f:c9  
          inet addr:188.xxx.xxx.xx  Bcast:188.xxx.xxx.xxx  Mask:255.xxx.xxx.xxx
          inet6 addr: fe80::21d:72ff:fe2c:9fc9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:380 errors:0 dropped:0 overruns:0 frame:0
          TX packets:140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27830 (27.8 KB)  TX bytes:14179 (14.1 KB)
          Interrupt:16 

ligita@ligita-laptop:~$ sudo lshw -c network
[sudo] password for ligita: 
  *-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:72:2c:9f:c9
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=full firmware=5787m-v3.23 ip=188.112.130.95 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:28 memory:f6000000-f600ffff
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth2
       version: 01
       serial: 00:1f:3a:b1:16:dd
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f8000000-f8003fff
ligita@ligita-laptop:~$ cat /sys/class/net/eth0/carrier
1
ligita@ligita-laptop:~$ 

Thanks you for your help!

---

### Post by Siilis on 2012-03-18
[Edit]
I thought I forgot a command, this post can be deleted, sorry.

---

### Post by matt_symes on 2012-03-18
Hi

**I have redacted your IP address. You may want to edit your previous post and do the same.**

> inet addr:188.xx.xxx.xxx Bcast:188.xxx.xxx.xxx Mask:255.xxx.xxx.xxx

Your IP address is not a private IP address. Are you behind a router or plugged directly into the internet ? 

Where are you getting your IP address from ?

Kind regards

---

### Post by Siilis on 2012-03-18
I have a broadband router. And I don't clearly understand, what do you mean from where I get my IP address?

---

### Post by chubbtech on 2012-03-18
when you say your network configs are same in both windows and linux boxes...hope you don't mean identical IPs

---

### Post by matt_symes on 2012-03-18
Hi

> **Siilis said:**
> I have a broadband router. And I don't clearly understand, what do you mean from where I get my IP address?

This is my set up

Internet -> Modem -> Router -> My computer.

My ISP gives my router an IP address. This is a **public** IP address and is how Internet traffic gets routed to my house.

My computers are connected to my router. My router give my computers a **private** IP address. This is of the form 192.168.1.X.

My router routes the traffic from the Internet using my public IP address and routes it to my computer using NAT and my computers private IP address.

The IP address on your computer looks like the public IP address my router has (i.e. it's not a private IP address).

Therefore, are you behind a router that gives you a private IP address or are you connected directly to the modem ?

Kind regards

---

### Post by Siilis on 2012-03-19
It's a public IP. I checked the router, it looks like it only shows if there is a internet connection, but doesn't do anything else to it, since removing the ethernet cable doesn't destroy the connection.

---

### Post by matt_symes on 2012-03-19
Hi

Is your route to your gateway set up correctly ?

You can check this with the route command.

```
route
```

Kind regard

---

### Post by Siilis on 2012-03-19
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
xxx.xxx.xxx.x   *               255.xxx.xxx.xxx U     1      0        0 eth0
link-local      *               255.xxx.x.x     U     1000   0        0 eth0

Is this correct? Sorry, but I don't know much about Linux :(.

---

### Post by matt_symes on 2012-03-19
Hi

You have no gateway set up.

```
Destination Gateway Genmask Flags Metric Ref Use Iface
xxx.xxx.xxx.x * 255.xxx.xxx.xxx U 1 0 0 eth0
link-local * 255.xxx.x.x U 1000 0 0 eth0
```

When i plug directly into my modem (not my router) my computer gets sent the gateway IP address via DHCP.

```
matthew@matthew-Aspire-7540:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:1f:16:c3:48:69  
          inet addr:62.xxx.xxx.39  Bcast:62.xxx.xxx.255  Mask:255.xxx.xxx.xxx
          inet6 addr: fe80::21f:16ff:fec3:4869/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:137 errors:0 dropped:0 overruns:0 frame:0
          TX packets:212 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:56569 (56.5 KB)  TX bytes:43102 (43.1 KB)
          Interrupt:16 

matthew@matthew-Aspire-7540:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
**0.0.0.0          62.xxx.xxx.1   0.0.0.0           [COLOR="Red"]UG[/COLOR]    0      0        0 eth0**
62.xxx.xxx.0    0.0.0.0         255.xxx.xxx.xxx   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0       U     1000   0        0 eth0
matthew@matthew-Aspire-7540:~$ 
```

The line highlighted in bold is the route to my (ISP) gateway. You can tell it the gateway by the UG highlighted in red. 

You do not seem to have one. Without one, Ubuntu will not know where to route traffic going outside your subnet.

Kind regards

---

### Post by Siilis on 2012-03-20
Thank you so much! So I just need to set up the gateway? Is there a specific command I should use or I can just go in the internet settings and do it from there?

---

### Post by Kenny85 on 2012-03-20
Check in your browser 
go file ->work online...
really common  mistake

---

### Post by Siilis on 2012-03-20
It didn't help. Still doesn't load any pages.

---

### Post by matt_symes on 2012-03-20
Hi

> Thank you so much! So I just need to set up the gateway? Is there a specific command I should use or I can just go in the internet settings and do it from there?

I'm not 100% sure this is your problem yet mind ;)

You need to find the IP address of your gateway. You can do this from windows also using the route command from the command prompt.

Something else i wanted to check though.

Right click on network manager (nm-applet)and choose edit connections. Select your wired connection (eth0).

Navigate to the IPv4 tab and look at the "method" dropdown control.

What's it set to ? 

Kind regards

---

### Post by Siilis on 2012-03-20
The method is Manual and the routes are empty, although, in the IPv4 Settings, the addresses are filled.

---

### Post by matt_symes on 2012-03-20
Hi

> The method is Manual

This is starting to make sense. 

You added a static IP address but did not add a gateway ?

Is there any reason you have it set to manual as opposed to Automatic (DHCP) ?

Kind regards

---

### Post by Siilis on 2012-03-20
Well I haven't changed anything since the 1st time I used the laptop and had to add the numbers, which was a long time ago. Don't remember if it should be set to manual. And I lost the connection while being on the laptop, don't think I pressed something, was busy with a project. Should I try if Automatic works?

---

### Post by matt_symes on 2012-03-20
Hi

Try this but first make a note of all the IP addresses.

Disconnect your wired connection. Remove RJ45 connector.

Right click on network-manager->edit connections->wired->ipv4->method.

Set this to Automatic (DHCP). Reboot PC (no real need to do this but...)

When booted up and logged in, reinsert the wired RJ45 connector.

Wait a minute. Open a terminal and type

```
ifconfig eth0
```

Check you have an IP address and such.

Type 

```
route -n
```

Check you have an entry UG.

Post back on how you get on.

Kind regards

---

### Post by Siilis on 2012-03-20
ligita@ligita-laptop:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:1d:72:2c:9f:c9  
          inet addr: xx.xxx.xx.xxx  Bcast: xx.xxx.xx.xxx  Mask:255.xxx.xxx.x
          inet6 addr: fe80::21d:72ff:fe2c:9fc9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12082 (12.0 KB)  TX bytes:7216 (7.2 KB)
          Interrupt:16 

ligita@ligita-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
xx.xxx.xx.x     0.0.0.0         255.xxx.xxx.x   U     1      0        0 eth0
xxx.xxx.x.x     0.0.0.0         255.xxx.x.x     U     1000   0        0 eth0
0.0.0.0         xx.xxx.xx.x(The same as the 1st destination)     0.0.0.0         UG    0      0        0 eth0


Done. I opened up my browser, now it shows that "We couldn't recognise your computer or give it a correct IP address." It also shows a identification code, client info numbers.

---

### Post by matt_symes on 2012-03-20
Hi

```
Destination Gateway Genmask Flags Metric Ref Use Iface
xx.xxx.xx.x 0.0.0.0 255.xxx.xxx.x U 1 0 0 eth0
xxx.xxx.x.x 0.0.0.0 255.xxx.x.x U 1000 0 0 eth0
0.0.0.0 xx.xxx.xx.x(The same as the 1st destination) 0.0.0.0 [COLOR="Red"]UG[/COLOR] 0 0 0 eth0
```

At least you now have a gateway. Is your IP address the same as before ?

BTW, Who is your ISP ?

Make a note of the gateway IP address. 

Go back into the network settings page and change back to manual. Put back the origanl values and add the gateway IP address under the routes.

See if that helps.

Kind regards

---

### Post by Siilis on 2012-03-20
Ok I tried that. I added all the addresses in IPv4 and in routes, but it still doesn't work. Also, do I have to add the Address and Netmask in routes? It doesn't allow me to apply the gateway if I don't. And what do I have to type in Metric?

[Edit] My ISP is a local provider called Lattelecom.

---

### Post by matt_symes on 2012-03-20
> Also, do I have to add the Address and Netmask in routes? It doesn't allow me to apply the gateway if I don't.

Yes, you do.

> And what do I have to type in Metric?

Put a 1 for the metric.

Give that a try.

> My ISP is a local provider called Lattelecom.

I don't know them.

> I opened up my browser, now it shows that "We couldn't recognise your computer or give it a correct IP address." It also shows a identification code, client info numbers.

I would have expected DHCP to have worked correctly for you and the above came as a surprise. I think the problem may be your gateway IP address.

If the worst comes to the worst, have you considered contacting them for technical support ?

Kind regards

---

