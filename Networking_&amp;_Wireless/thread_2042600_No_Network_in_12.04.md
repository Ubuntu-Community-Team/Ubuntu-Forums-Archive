---
title: "No Network in 12.04"
date: 2012-08-15
forum: Networking &amp; Wireless
---

### Post by juanbisente on 2012-08-15
Hi!!

Can anyone help me? I have installed Ubuntu 12.04 but I cant connect to the internet and in LAN. I can't even Ping network computers. I have checked my DNS, NIC and cables it all work fine. I have browse a lot of threads but no one works for me.

Appreciate your response, thanks

---

### Post by juanbisente on 2012-08-15
Here are some generated outputs for your reference:

sudo lspci
> 02:03.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)

sudo lshw -C Network
>   *-network               
       description: Ethernet interface
       product: NC100 Network Everywhere Fast Ethernet 10/100
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 11
       serial: 00:08:a1:41:50:3a
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 ip=192.168.10.120 latency=64 maxlatency=128 mingnt=64 multicast=yes
       resources: irq:10 ioport:2000(size=256) memory:d5100000-d51003ff memory:20000000-2001ffff

iwconfig 
> lo        no wireless extensions.

eth0      no wireless extensions.

ifconfig 
> eth0      Link encap:Ethernet  HWaddr 00:08:a1:41:50:3a  
          inet addr:192.168.10.120  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::208:a1ff:fe41:503a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:562 overruns:0 frame:0
          TX packets:0 errors:239 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:766 errors:0 dropped:0 overruns:0 frame:0
          TX packets:766 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:77461 (77.4 KB)  TX bytes:77461 (77.4 KB)

---

### Post by dandnsmith on 2012-08-15
The lack of wireless extensions (previous post) is expected with a wired-only system.
Do you get the IP address via DHCP (ie automatically?)
What leads you to assert that the DNS and IP stuff is working, as I would only say that if (for example) I could access internet sites with a browser?

If you can use the browser, then there may be firewalling stopping use of Ping etc - there are a lot of things which might go wrong.

I suggest you try to post some more info about what you've tried and what works (or doesn't), and also include some brief notes about how your local network is set up (for example, mine has a number of PCs running both Windows and Ubuntu/Mint, wired to a router which provides NAT and access to the internet).

---

### Post by juanbisente on 2012-08-16
sorry I didn't mention that it was an upgrade from ubuntu 10.04 to 12.04 that is why I know that the dns and ip is working because I use the same config.

It is a static ip not DHCP.

---

### Post by albandy on 2012-08-16
> **juanbisente said:**
> sorry I didn't mention that it was an upgrade from ubuntu 10.04 to 12.04 that is why I know that the dns and ip is working because I use the same config.

It is a static ip not DHCP.

Well dns has changed. Now you cannot use resolv.conf directly.

To test if this is the cause of your problems, open a browser and type:

[http://74.125.230.216](http://74.125.230.216)

If google appears is a dns configuration problem

---

### Post by juanbisente on 2012-08-16
Sure I'll  Try it.

But I guess it is not DNS Problem because I can't even PING a computer in my LAN. And I am using same DNS config to my other computer and they can acces internet and LAN computers. The only difference is that my other computers uses On Board LAN this one uses NIC.

---

### Post by satish_j on 2012-08-16
Is the nm-applet showing disconnected??
I faced similar problem on fresh install of 12.04.edited the file /etc/network manager/network manager.conf to replace **managed= false** to **managed=true** somewhere at the last line in ifupdown section,rebooted and issue was resolved.

---

### Post by juanbisente on 2012-08-17
the network manager applet says device not manage

---

### Post by albandy on 2012-08-17
I think it could be a negotiation problem, I saw this errors in one of your posts:
RX packets:0 errors:0 dropped:562 overruns:0 frame:0
TX packets:0 errors:239 dropped:0 overruns:0 carrier:0

Type this: sudo mii-tool eth0
and post the result.

---

### Post by juanbisente on 2012-08-17
here is the result for

sudo mii-tool eth0> eth0: negotiated 100baseTx-FD flow-control, link ok

---

### Post by albandy on 2012-08-17
> **juanbisente said:**
> here is the result for

sudo mii-tool eth0

This looks ok, you're working at 100Mbit/s full duplex.

I readed that you're using static ip. Can you switch to dhcp to test it?

---

### Post by juanbisente on 2012-08-17
what commands should I run after I switch to dhcp?

---

### Post by albandy on 2012-08-17
> **juanbisente said:**
> what commands should I run after I switch to dhcp?

Don't need to change anything. You can type:
sudo dhclient eth0
and if works you will get a new ip.

but this don't change anything, when you reboot your static ip will appear again.

---

### Post by juanbisente on 2012-08-17
I switch from static to DHCP using
> sudo nano /etc/network/interfacesthen I run
> sudo /etc/init.d/networking restartthen i have the result
> failed to bring up eth0

---

### Post by albandy on 2012-08-17
> **juanbisente said:**
> I switch from static to DHCP using
then I run
then i have the result

Try this:

sudo ifconfig eth0 up
sudo dhclient eth0

edited:
also do this and post the result:
cat /etc/udev/rules.d/70-persistent-net.rules

---

### Post by juanbisente on 2012-08-17
> sudo ifconfig eth0 up
sudo dhclient eth0didn't return any result

cat /etc/udev/rules.d/70-persistent-net.rules
> SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:08:a1:41:3a", ATTR{dev_id}=="0x0" ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

---

### Post by albandy on 2012-08-17
OK, edit /etc/udev/rules.d/70-persistent-net.rules and change from this:
```

SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:08:a1:41:3a", ATTR{dev_id}=="0x0" ATTR{type}=="1", KERNEL=="eth*", NAME="eth0" 

```
to this:
```

SUBSYSTEM=="net", ACTION=="add", DRIVERS=="tulip", ATTR{address}=="00:08:a1:41:3a", ATTR{dev_id}=="0x0" ATTR{type}=="1", KERNEL=="eth*", NAME="eth0" 

```

then reboot.
If this not work, empty the file and it will be regenerated on next boot.

---

### Post by juanbisente on 2012-08-17
It didn't work, I also tried emptying the file still didn't fix the problem

---

### Post by albandy on 2012-08-17
Maybe the easiest way is to change your card. I don't know how expensive can be a network card  in your contry but usually a 1000Mbit realtek card is less than 10&#8364;.

---

### Post by juanbisente on 2012-08-17
Is that the only way?
well, I'll try to replace it.
thank you very much.

---

### Post by satish_j on 2012-08-18
have you checked the file /etc/network manager/network manager.conf.pls post the contents of this file..

---

