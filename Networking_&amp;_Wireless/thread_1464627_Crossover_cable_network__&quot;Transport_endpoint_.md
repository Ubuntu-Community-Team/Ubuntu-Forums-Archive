---
title: "Crossover cable network:  &quot;Transport endpoint is not connected&quot;"
date: 2010-04-28
forum: Networking &amp; Wireless
---

### Post by TheHimself on 2010-04-28
I have to move gigabites of stuff between two laptops. I set up a manual network with


ip address 10.42.43.1
network mask: 255.255.255.0
Gateway: 10.42.43.255

on the 'source' computer and with


ip address 10.42.43.2
network mask: 255.255.255.0
Gateway: 10.42.43.255


on the other one. Then connect the two computers using a corossover cable  and then use sshfs. The file system of the 'source' is mounted successfully but as soon as I want to copy something, it  gets unmounted and I get the error 

"Transport endpoint is not connected".

 I googled the error message but didn't find anything helpful. Your help is appreciated.

---

### Post by Iowan on 2010-04-28
Gateway address? Dunno if the broadcast address is adequate, or if you should cross-couple (list the other machine's address as gateway). 

Really shouldn't matter in the same subnet...
After the fault, can you still ping the other machines? Some threads suggest that a high load can cause the network/connection/card to shut down.

---

### Post by TheHimself on 2010-04-28
Yes, I can ping. Just the remote drive gets unmounted and I can mount it again without having to reset the network. (though the same thing happens again.)

---

### Post by capscrew on 2010-04-28
> **TheHimself said:**
> I have to move gigabites of stuff between two laptops. I set up a manual network with


ip address 10.42.43.1
network mask: 255.255.255.0
Gateway: 10.42.43.255

on the 'source' computer and with


ip address 10.42.43.2
network mask: 255.255.255.0
Gateway: 10.42.43.255


on the other one. Then connect the two computers using a corossover cable  and then use sshfs. The file system of the 'source' is mounted successfully but as soon as I want to copy something, it  gets unmounted and I get the error 

"Transport endpoint is not connected".

 I googled the error message but didn't find anything helpful. Your help is appreciated.

The broadcast address of the network which you have described as 10.42.43.0 /24 (the subnet mask does this as 255.255.255.0) means that the broadcast address is 10.42.43.255.  This means it can't be the default gateway.  The gateway is where packets are sent when no local MAC address destination is discovered.  You do not need a default gateway anyway as you are not internetworking (transiting multiple IP networks).

Try your setup without a default gateway in the config.

---

### Post by TheHimself on 2010-04-29
But network manager doesn't let me do so.

---

### Post by capscrew on 2010-04-29
> **TheHimself said:**
> But network manager doesn't let me do so.

Then use a number that is not 10.42.43.255.  How about 10.42.43.2 ?

---

### Post by TheHimself on 2010-04-30
Thank you. That didn't solve the problem but I found a clue. When using scp I get the message:

```
isconnecting: Corrupted MAC on input.
lost connection
```

In the network manager the "MAC address" field is blank for the connections. 
Can the problem be related to the fact that one of the machines is 32 bit and the other is 64 bit (with corresponding Ubuntu's)?

---

### Post by capscrew on 2010-04-30
> **TheHimself said:**
> Thank you. That didn't solve the problem but I found a clue. When using scp I get the message:

```
isconnecting: Corrupted MAC on input.
lost connection
```

In the network manager the "MAC address" field is blank for the connections. 
Can the problem be related to the fact that one of the machines is 32 bit and the other is 64 bit (with corresponding Ubuntu's)?

No, the 32/64 has nothing to do with it.  But the "Corrupted MAC" has everything to do with the problem.  The MAC address is the hardware address of the NIC (the network card (interface)).

Thinking...

**Edit 3:  I see MY mistake.  I told you to make the gateway 10.42.43.2 and I meant _[COLOR="Red"]10.42.43.25[/COLOR]_.  Try this updated gateway before doing anything more.**

Edit2:  The hardware address (MAC) is really what the 2 laptops communicate with.  You need the IP address but it is bound to the MAC address.  ARP (address resolution protocol) is used to hand off the data packets to the proper interface.

Edit:  Can you post output of ```
ifconfig -a
``` and maybe ```
arp -a
```for both hosts (laptops)?

---

### Post by TheHimself on 2010-04-30
With the new gateway address I get the error again. Strangely I get the message after a few files are copied.

This is the output for the computer on which openssh-server is installed:
```



eth0      Link encap:Ethernet  HWaddr 00:23:8b:94:4d:c5  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::223:8bff:fe94:4dc5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:313 errors:0 dropped:0 overruns:0 frame:0
          TX packets:627 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27275 (27.2 KB)  TX bytes:814002 (814.0 KB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:23:4e:e0:1a:43  
          inet6 addr: fe80::223:4eff:fee0:1a43/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:787 errors:0 dropped:0 overruns:0 frame:0
          TX packets:787 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:254920 (254.9 KB)  TX bytes:254920 (254.9 KB)


rez@rez-laptop:~$ sudo arp -a
rez-laptop.local (10.42.43.2) at 00:1d:72:8e:d2:89 [ether] on eth0

```

And for the other computer:
```

eth0      Link encap:Ethernet  HWaddr 00:1d:72:8e:d2:89  
          inet addr:10.42.43.2  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:72ff:fe8e:d289/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17554 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11008 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:19846605 (19.8 MB)  TX bytes:1180602 (1.1 MB)
          Memory:fe000000-fe020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:840 errors:0 dropped:0 overruns:0 frame:0
          TX packets:840 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:796662 (796.6 KB)  TX bytes:796662 (796.6 KB)

pan0      Link encap:Ethernet  HWaddr 72:0d:5b:ae:97:66  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:6f:9e:60  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:72473 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45162 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:85308719 (85.3 MB)  TX bytes:5550489 (5.5 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-6F-9E-60-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

rez@rez-laptop:~$ sudo arp -a
rez-laptop-2.local (10.42.43.1) at 00:23:8b:94:4d:c5 [ether] on eth0


```

---

### Post by capscrew on 2010-04-30
> **TheHimself said:**
> With the new gateway address I get the error again. Strangely I get the message after a few files are copied.

So let's look carefully and the interface info.  Do we have correct IP addresses?
> 
This is the output for the computer on which openssh-server is installed:

```

eth0      Link encap:Ethernet  HWaddr [COLOR="Blue"]**00:23:8b:94:4d:c5**[/COLOR]  
          inet addr:10.42.43.1  Bcast:10.42.43.255  

```

And for the other computer:


```

eth0      Link encap:Ethernet  HWaddr [COLOR="Teal"]**00:1d:72:8e:d2:89**[/COLOR]  
          inet addr:10.42.43.2  Bcast:10.42.43.255  Mask:255.255.255.0

```

ARP from the first laptop gets the second laptops MAC addr

```
rez@rez-laptop:~$ sudo arp -a
rez-laptop.local (10.42.43.2) at [COLOR="Teal"]00:1d:72:8e:d2:89[/COLOR] [ether] on eth0

```


And ARP from the second Laptop shows the first laptop's MAC addr

```
rez@rez-laptop:~$ sudo arp -a
rez-laptop-2.local (10.42.43.1) at [COLOR="Blue"]00:23:8b:94:4d:c5[/COLOR] [ether] on eth0

```

This shows that the interfaces are correctly configured at this point.  I believe that one (or both) NIC drivers have been corrupted and you should reinstall the drivers.

You might post results of the show hardware command for both hosts.  That would be```
lshw
```

---

### Post by TheHimself on 2010-04-30
Thank you for you attention. The addresses are correct (I mean correspond to the correct computer). This is the result of lshw for the client computer.

```
*-network
             description: Ethernet interface
             product: 82566MM Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 03
             serial: 00:1d:72:8e:d2:89
             capacity: 1GB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 firmware=0.3-0 latency=0 link=no multicast=yes port=twisted pair
             resources: irq:27 memory:fe000000-fe01ffff memory:fe025000-fe025fff ioport:1840(size=32)
        
```

---

### Post by capscrew on 2010-04-30
> **TheHimself said:**
> Thank you for you attention. The addresses are correct (I mean correspond to the correct computer). This is the result of lshw for the client computer...

I don't see anything wrong there either.

To be really thorough you should add a switch between the 2 laptops.  Have you checked the cable to make sure it is correct and also that it not faulty?

Other than that I am truly stumped.  Maybe reinstall the drivers.  I've never had to reinstall component so I really shouldn't commenting here as it just guessing.

Sorry I could not help you.  Sometimes a USB flash drive is your best friend.

---

