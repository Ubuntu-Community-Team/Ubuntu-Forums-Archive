---
title: "eth0 not found"
date: 2011-08-06
forum: Networking &amp; Wireless
---

### Post by mehta_4v on 2011-08-06
Hello. I am working with ubuntu and my eth0 connection was up and working fine untill some days back when all of a sudden it seemed to disapper. I was able to access the net through it before. But now it has vanished and i donno when. i tried ifconfig eth0 up but no use. The result of  cat /etc/network/interfaces is as follows

auto lo
iface lo inet loopback


Can anyone figure out the problem?

---

### Post by x-D on 2011-08-06
This may seem like a stupid question, but have you tried unplugging the ethernet and plugging it in, restarting the router, and restarting the computer yet?

---

### Post by mehta_4v on 2011-08-06
Ya everything is fine and the ethernet works in windows. Actually i m using virtual box VMWare and ubuntu is my guest operating system. Thanks

---

### Post by mehta_4v on 2011-08-06
Just for an update i typed the following command and futher follows the output:

sudo lshw -C network

*-network               
       description: Ethernet interface
       product: 79c970 [PCnet32 LANCE]
       vendor: Advanced Micro Devices [AMD]
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth1
       version: 10
       serial: 00:0c:29:f0:f3:30
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master rom ethernet physical logical tp 1000bt-fd
       configuration: autonegotiation=off broadcast=yes driver=vmxnet driverversion=2.0.4.0 duplex=full firmware=N/A latency=64 link=yes maxlatency=255 mingnt=6 multicast=yes port=twisted pair speed=1GB/s
       resources: irq:19 ioport:2000(size=128) memory:dc400000-dc40ffff(prefetchable)


It seems that eth1 is present. Itried doing

ifconfig eth1 up

but that doesnt help either. Please help.

---

### Post by x-D on 2011-08-06
Right... have you installed any new packages or done any upgrades recently, anything at all? Have you edited anything in Windows? Made any changes in Virtual Box whatsoever?

---

### Post by x-D on 2011-08-06
Have you actually made any changes to the system recently? Try to connect to eth1 if you can and see if that works then?

---

### Post by mehta_4v on 2011-08-06
Nope. No editing and all. Everything same as before. As ethernet doesnt work i am not able to updat-upgrade or install any new packages.

---

### Post by mehta_4v on 2011-08-06
How do i connect to eth1?? Sorry no idea. I said i tried 

ifconfig eth1 up

but of no use. Do I need to do something else also?

---

### Post by x-D on 2011-08-06
Well, you said that eth1 is working right, if that is the case then you would need to do:

```

sudo ifdown eth0

```

```

sudo ifdown eth1

```

```

sudo ifup eth1

```

Or download networkmanager7 that may help, I won't be able to help until around 5:30 (7 hours time if your somewhere else) so please be patient!

---

### Post by x-D on 2011-08-06
To enable a network connection:

Press Applications &#8594; Accessories &#8594; Terminal to open a Terminal

Type sudo ifdown eth1 in the Terminal and press Return, replacing eth1 with the name of your network interface if it is different

Enter your password if prompted

Type sudo ifup eth1 in the Terminal and press Return, again replacing eth1 with the name of your network interface

If you have connected successfully, you should see a message similar to the following (the numbers may be different):

DHCPACK from 192.168.2.1
bound to 192.168.2.4 -- renewal in 536349522 seconds.

---

### Post by x-D on 2011-08-06
> **x-D said:**
> To enable a network connection:

Press Applications &#8594; Accessories &#8594; Terminal to open a Terminal

Type sudo ifdown eth1 in the Terminal and press Return, replacing eth1 with the name of your network interface if it is different

Enter your password if prompted

Type sudo ifup eth1 in the Terminal and press Return, again replacing eth1 with the name of your network interface

If you have connected successfully, you should see a message similar to the following (the numbers may be different):

DHCPACK from 192.168.2.1
bound to 192.168.2.4 -- renewal in 536349522 seconds.

Taken from an official Ubuntu help page. Try networkmanager0.7 if this doesn't work! :)

---

### Post by dineshs on 2011-08-06
Can you run ```
sudo dhclient eth1
```and post the result of ```
ifconfig -a
```

---

### Post by x-D on 2011-08-06
> **dineshs said:**
> Can you run ```
sudo dhclient eth1
```and post the result of ```
ifconfig -a
```

Let's wait to see if my simple fix works first (it may or may not do - fingers crossed) :P :LOL:

---

### Post by mehta_4v on 2011-08-06
@ x- D

These are the outcome of the commands you suggested:

1) sudo ifdown eth0

[sudo] password for charvi123: 
ifdown: interface eth0 not configured


2)    sudo ifdown eth1
ifdown: interface eth1 not configured


3)   sudo ifup eth1
Ignoring unknown interface eth1=eth1.

:icon_frown:
What does this mean?

---

### Post by mehta_4v on 2011-08-06
Hey first of all thank you to both of you.

@ dineshs
It worked!! I got the following prints just as x- D said.

DHCPACK of 10.100.3.27 from 10.100.3.7
bound to 10.100.3.27 -- renewal in 570319 seconds.

and also ifconfig -a shows the following:

eth1      Link encap:Ethernet  HWaddr 00:0c:29:f0:f3:30  
          inet addr:10.100.3.27  Bcast:10.100.3.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fef0:f330/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:76792 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5657215 (5.6 MB)  TX bytes:4317 (4.3 KB)
          Interrupt:19 Base address:0x2024 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:212 errors:0 dropped:0 overruns:0 frame:0
          TX packets:212 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15988 (15.9 KB)  TX bytes:15988 (15.9 KB)


But if I try the same with eth0 it doesnt work. It gives:

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device


Can you please explain me what does this command do actually? And why isnt it working with eth0 when eth0 worked fine until some days back? Thanks in advance.

---

### Post by mehta_4v on 2011-08-06
Hey problem not solved yet.

When after trying the above solution i rebooted my PC then the ifconfig did not show the eth1. Why?? Is there no permenant solution. Before this when I worked with the eth0 up I did not have to start it every time i botted up..... Please Help.... :confused:

---

### Post by mehta_4v on 2011-08-06
I figured it out.

What I did was following:

$ sudo vim /etc/udev/rules.d/70-persistent-net.rules

Edited this file from eth1 to eth0 in the vmxnet section so that the contents of the file looked as follows:

# PCI device 0x1022:0x2000 (pcnet32)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:0c:29:f0:f3:26", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x1022:0x2000 (vmxnet)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:0c:29:f0:f3:30", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

Save this file and exit.

Reboot the system with $sudo reboot.

And now the eth0 works everytime as expected and also shows up in ifconfig.
(Although I don't get the symbol in the menu bar above.):D

---

### Post by x-D on 2011-08-06
> **mehta_4v said:**
> I figured it out.

What I did was following:

$ sudo vim /etc/udev/rules.d/70-persistent-net.rules

Edited this file from eth1 to eth0 in the vmxnet section so that the contents of the file looked as follows:

# PCI device 0x1022:0x2000 (pcnet32)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:0c:29:f0:f3:26", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x1022:0x2000 (vmxnet)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:0c:29:f0:f3:30", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

Save this file and exit.

Reboot the system with $sudo reboot.

And now the eth0 works everytime as expected and also shows up in ifconfig.
(Although I don't get the symbol in the menu bar above.):D

Good, good, well done for fixing it... glad I was of some help to you :) glad to see my commands lead you along the right path to fixing it hehe ;) :guitar:

Cheers, 

x-D

---

