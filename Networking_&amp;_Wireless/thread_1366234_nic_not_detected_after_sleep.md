---
title: "nic not detected after sleep"
date: 2009-12-28
forum: Networking &amp; Wireless
---

### Post by prconnor@gmail.com on 2009-12-28
Hello,

Just upgraded to 9.10.  Have my computer set to sleep when idle for a period.  Now when it wakes the ethernet card is not detected.

I can still connect to wireless, but no nic, which is the normal way that I connect

ifconfig says:

```
eth1      Link encap:Ethernet  HWaddr 00:09:5b:68:4b:44  
          inet addr:192.168.1.118  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::209:5bff:fe68:4b44/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1909 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1432 errors:2 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2213481 (2.2 MB)  TX bytes:240440 (240.4 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1440 (1.4 KB)  TX bytes:1440 (1.4 KB)

```

not visible is eth0, which is my nic. 'System' -> 'Administration' -> 'Network Tools' lists eth0 with a state of inactive.

lshw lists this for eth0
```
 *-network:1 DISABLED
                description: Ethernet interface
                product: 82801DB PRO/100 VE (LOM) Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:02:08.0
                logical name: eth0
                version: 81
                serial: 00:03:47:fd:22:50
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A latency=32 maxlatency=56 mingnt=8 multicast=yes
                resources: irq:20 memory:feaa9000-feaa9fff ioport:d000(size=64)
```

tried to run ```
/etc/init.d/network restart
/etc/init.d/network-manager restart
``` as root, but that didn't fix my problem either.

Thank you for your help.

---

### Post by prconnor@gmail.com on 2009-12-28
Now a restart of my computer did not even restore my wired interface, but ...

I have had some success:

```
sudo ethtool -r eth0 
sudo ifconfig eth0 up
```

both had exit status 0, and displayed no information.  After this I could see my nic listed with the ```
ifconfig
``` command, but it was not associated with my network.

I then created a new wired connection in network manager (Right click on the taskbar symbol, choose edit connections.) and now it is up.  No data yet if it is persistent, or if it will work after going to sleep.

Maybe it has something to do with keyring that I had to authorize when I performed this last step.

---

### Post by brianpatrick on 2010-01-04
The ubu elves completely trashed all of the old, standard network tools:

root@trex:/tera/bak# ifup eth1
ifup: interface eth1 already configured
root@trex:/tera/bak# ifdown  eth1
Ignoring unknown interface eth1=eth1.
First, they tell you the interface is "already configured" and then go on to say that it is an "unknown interface". Which is it? Consistency bug for sure. 

Next bug:
root@trex:/tera/bak# /etc/init.d/networking  start
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service networking start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start networking
networking stop/waiting

OK. Let's try their advice:
root@trex:/tera/bak# service networking start
networking stop/waiting
And, nothing happens

OK. Let's try their other advice:
root@trex:/tera/bak# start networking
networking stop/waiting
And, again, nothing happens. 

Then do system -> preferences -> network connections -> eth1 -> ipv4:
Check your IP (static?), mask, gateway, routes, ... and apply...
Again, nothing happens whatsoever. 

Falling back on another old school trick:
root@trex:/tera/bak# ifconfig | grep 'inet addr'
          inet addr:127.0.0.1  Mask:255.0.0.0
root@trex:/tera/bak# ifconfig eth1 up
root@trex:/tera/bak# ifconfig | grep 'inet addr'
          inet addr:127.0.0.1  Mask:255.0.0.0
root@trex:/tera/bak# 
Nothing happens.......

You, as root, order it to do something. It does nothing and does not even bother to do the common courtesy of giving you an informative error message. These little knuckleheads have some real chutzpa!

I have yet to find any command line incantation which works on ubu 9.10. That sucks. Please, some network guru enlighten me. 

After much hair pulling and cussing of cutesy elves who like to show how smart they are by reinventing their own version of a wheel and destroying all existing wheels, I stumbled upon this trick:
Find the network connection icon on top of the screen (2 displays with an X in front), click it, then click 'auto_eth1'. 

Voila!
root@trex:/tera/bak# ifconfig | grep 'inet addr'
inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
inet addr:127.0.0.1  Mask:255.0.0.0

I want to crazy glue the door locks on their cars and tell them to use the trunk instead!!! (^_^)

    BrianP

---

