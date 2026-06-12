---
title: "Wireless Networking goes in and out."
date: 2006-01-06
forum: Networking &amp; Wireless
---

### Post by endokrin on 2006-01-06
Hi I have ubuntu running on my Gateway M320 laptop with a built-in ethernet and wireless card.

For a couple months, I had no problem with my wireless connection.  The past few weeks, I've had problems.  Sometimes, on startup, it won't connect.  Other times, I will be surfing the net for 10 min, 30 min, or an hour, etc.  and the wireless connection will suddenly go down.  I am then forced to restart my computer to get it working again.

I have not changed any of the settings on my router, and that seems to be working fine.  This happens regardless of being 50 ft. from the router or 5 inches from it.  I have also ruled out interference from other devices like a cordless phone.

Here is some info I hope might help:

```

user@ubuntu:~$ ifconfig eth1
eth1      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:35ff:fe8b:2303/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1722 errors:0 dropped:0 overruns:0 frame:0
          TX packets:867 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2432701 (2.3 MiB)  TX bytes:43935 (42.9 KiB)
          Interrupt:10 Base address:0x2000 Memory:e0200000-e0200fff

```

(XX:XX... I removed the numbers for security)

```

user@ubuntu:~$ lspci | grep Eth
0000:02:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

```

user@ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1

```

```

user@ubuntu:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth1

# The primary network interface
iface eth1 inet dhcp
        # wireless-* options are implemented by the wireless-tools package
        wireless-mode managed
        wireless-essid linksys
        wireless-key XXXXXXXXXXXXXXXXXXXXXX

auto eth1

```

```

user@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr XXXXXXXXXXX
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0x3000

eth1      Link encap:Ethernet  HWaddr XXXXXXXXXXXX
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:35ff:fe8b:2303/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21531 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22164 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:14971009 (14.2 MiB)  TX bytes:13977651 (13.3 MiB)
          Interrupt:10 Base address:0x2000 Memory:e0200000-e0200fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4728 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4728 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:373274 (364.5 KiB)  TX bytes:373274 (364.5 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


```

This is all right after startup, when the wirless connection is working.

I will post the code again when it stops working to see if anything changed... I don't know if that would help, I'm new at this.

Thanks!

---

### Post by endokrin on 2006-01-18
Well I am still having the problems.

I may have found a pattern:

If I am doing only one thing online, the connection seems to last the longest.

If I am only surfing the net it lasts a while.  But if I am surfing and downloading via Azureus, it goes out quicker.  Likewise, if I am only using Azureus and leave the computer to itself, the connection has lasted a few hours.  

I THINK that if I am using gaim, surfing AND Azureus, it goes out the quickest.

Any ideas?  It's like the connection gets stuck or something and I have to restart to get it to work.

Thanks.

---

### Post by GQed76 on 2006-01-19
are you using NDISwrapper?

If so they have a new version 1.8.  I'd update that then fiddle with drivers.

Not sure why it would just stop working for you.  Did you meddle with the firewall, firestarter?

---

### Post by bschuteker on 2006-01-26
Has anyone found any resolution on this?

I have the same problem. wireless is working fine, sometimes 5 minutes, sometimes 5 hours, then it just quits. If I plug a cable in to the same router and activate that connection it will work. Then sometime later I unplug and reactivate the wireless and it works again. The last time it quit working I just tried to reboot and it took a long time on the setting up network prompt and then errored out on the syncing to the time server. It gave an error of name resolution. This made me think...

When it would quit working FX would hang on the "looking up ???" instead if saying not able to open page. Could this have something to do with DNS? I'm better with the GUI than terminal but all my settings look correct. If someone can tell me what cammands to look at I will.

Thanks,

Bill

Oh, Wireless is Intel Pro 2200B/G no ndis wrapper used. Brezzy recognized it at installation

---

### Post by trubblemaker on 2006-02-01
I"m on a gatway with broadcom driver 4318, currently on Dapper using the new native driver bcm43xx driver and I used to get a signal with 
```
sudo iwconfig rate 11M
```
that used to get me a connection and it was stable 2 weeks ago after the most recent updates I"m now in your world of connectivity drops, like 2 mins after I succesfullly get an IP. Then I lose connection and after repeating the steps to get the ip back a few times I finally have the card crash
```
dmesg
```
says
```
bcm43xx: [..stuff..] Card not responding to IRQ. givin up.
```
what's your dmesg say when it dies?

---

### Post by mesri on 2006-08-16
I have a very similar problem on Dapper -- sometimes during bootup the system stops for a very long time on "Configuring Network Interfaces", but then says the process was "Ok", the system completes the bootup and the wireless connection is down.

Sometime rebooting brings it back, sometimes not.  If not, I often have to give up and run in WinXP for a while.

Or I'll be working fine for anywhere from 5 minutes to several hours, when the connection will suddenly disappear.

I'm using a Broadcom 4318, but with ndiswrapper.  Can't get to any other settings just yet as this is the only machine I've got right now.

---

### Post by firedoc on 2006-08-16
I've exactly the same problem as above. Happens both on the Ethernet and Wireless through a Linksys broadband router. I'm on a Sony Vaio Laptop with all latest updates  :-k

---

