---
title: "A Puzzling and Bizarre Wireless Problem"
date: 2006-01-19
forum: Networking &amp; Wireless
---

### Post by Vengeful Cynic on 2006-01-19
Yes, I know, I've heard it 100 places.  Every linux user who attempts to do wireless starts out with problems.  I am no different.... I am not a beautiful and unique snowflake.  However, my problem is bizarre... hopefully enough to pique your interest.

So what is my sad tale?  I'm glad you asked.

As best I can tell, the Aetheros drivers are working just fine on my Linksys WPC55AG. 

lspci | grep Ethernet yields:

```
Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
```

iwconfig yields:

```
ath0      IEEE 802.11  ESSID:"plugnplay"
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:0F:66:1A:4E:D7
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

But here's where it gets fun...

1) iwlist ath0 scan actually yields local networks (including the one that I'm configured to connect to

2) connecting to the wireless router leaves the router with a DHCP entry for my computer and an ip address

3) my computer can't find said ip address and can't route out using the wireless router, (disabling eth0 renders me connectionless)

so yeah... HELP!

-Vengeful Cynic

---

### Post by Lambert on 2006-01-20
With wired nic down and after trying to connect with wireless device, post the output of these commands

```

ifconfig
route
arp -a

```

---

### Post by Tea on 2006-01-21
Hi,

I think I've had the same problem, and I'd really like to know how to fix it.

So....bump?

Thanks

---

### Post by traherom on 2006-01-22
Bump from me too... I had the wireless working this morning for about an hour, then decided I was going to try to turn encryption back on... haven't been able to do anything beyond what the first post says, even after turning encryption back off...

iwconfig shows a full connection, but I'm unable to access the network. A ping to the router returns:
> ryan@ramlap:~$ ping -I wlan0 192.168.1.254
PING 192.168.1.254 (192.168.1.254) from 192.168.1.3 wlan0: 56(84) bytes of data.ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

--- 192.168.1.254 ping statistics ---
7 packets transmitted, 0 received, 100% packet loss, time 5998ms
 Even doing the ping under sudo doesn't help.

--EDIT--
And the output of those commands:
> ryan@ramlap:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2214 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2214 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:260975 (254.8 KiB)  TX bytes:260975 (254.8 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:90:4B:C2:28:7B
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::290:4bff:fec2:287b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:621 errors:0 dropped:0 overruns:0 frame:0
          TX packets:456 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:254627 (248.6 KiB)  TX bytes:92103 (89.9 KiB)
          Interrupt:18 Memory:dfffa000-dfffc000

ryan@ramlap:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 wlan0
default         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
ryan@ramlap:~$ arp -a
? (192.168.1.254) at 00:E0:98:55:A2:4A [ether] on wlan0
ryan@ramlap:~$
Hm... after taking the wired down to run those, I now have a connection... when I was doing it before, arp -a returned nothing. Odd...

---

### Post by Vengeful Cynic on 2006-01-24
ifconfig yields:

```
ath0      Link encap:Ethernet  HWaddr 00:0C:41:15:79:E7
          inet6 addr: fe80::20c:41ff:fe15:79e7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:36 errors:1804 dropped:0 overruns:0 frame:1804
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:2448 (2.3 KiB)  TX bytes:9646 (9.4 KiB)
          Interrupt:10 Memory:e0c80000-e0c90000

```

route yields an empty routing table

and 
arp -a just kicks back a carriage return


Vengeful Cynic

---

### Post by Lambert on 2006-01-24
[quote=Vengeful Cynic]ifconfig yields:

```
ath0      Link encap:Ethernet  HWaddr 00:0C:41:15:79:E7
          inet6 addr: fe80::20c:41ff:fe15:79e7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:36 errors:1804 dropped:0 overruns:0 frame:1804
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:2448 (2.3 KiB)  TX bytes:9646 (9.4 KiB)
          Interrupt:10 Memory:e0c80000-e0c90000

``` 
route yields an empty routing table

and 
arp -a just kicks back a carriage return


Vengeful Cynic[/quote]

Have you tried the command

sudo dhclient atho

Also is there anything in /var/lib/dhcp3/dhclient.leases

And can you post your /etc/dhclient.conf file here.

---

### Post by senning on 2006-01-31
Hey Lambert, I'm having pretty much the same problem (after it worked fine for about a half month) so I hope this helps:

In dhclient.leases:
> lease {
  interface "ath0";
  fixed-address 192.168.2.102;
  option subnet-mask 255.255.255.0;
  option dhcp-lease-time -1;
  option routers 192.168.2.1;
  option dhcp-message-type 5;
  option dhcp-server-identifier 192.168.2.1;
  option domain-name-servers 192.168.2.1;
  renew 2 2038/1/19 03:14:07;
  rebind 2 2038/1/19 03:14:07;
  expire 2 2038/1/19 03:14:07;
}


and it looks like I don't have an /etc/dhclient.conf file...

---

### Post by Vengeful Cynic on 2006-02-14
So, an update from the great beyond.  After beating my head against this computer for so long and getting almost-but-not-quite there, I decided that it was possible that the number of different wifi packages that I had tried, in conjunction with the simple fact that I hadn't run the install with the wifi card in led me to do a wipe and reinstall.

Post-install, I had the same sort of difficulties, until I grabbed Wifi Radar and ran it on a clean setup... and that cleared up my problems.

Now it just becomes a simple question of transferring these settings so that my wifi loads at start-up every time, without additional configs.  And while I wouldn't be opposed to shove in the right direction there, I'll get cracking on that now.

Thanks for all of the help and pushes in the right direction thus far.

---

