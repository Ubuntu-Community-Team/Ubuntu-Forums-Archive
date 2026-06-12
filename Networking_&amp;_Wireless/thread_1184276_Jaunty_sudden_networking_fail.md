---
title: "Jaunty sudden networking fail"
date: 2009-06-11
forum: Networking &amp; Wireless
---

### Post by mrdek11 on 2009-06-11
Hi there! I successfully set up a family MythTV box running Jaunty in early May.
Everything has been virtually smooth, until today. MythTV froze while watching a recording, so we rebooted. Now, no networking works. I cannot even ping localhost.
I am connected to the router via ethernet (eth0).
```
sudo dhclient
```
binds me to my DHCP IP, and acts normally, but I cannot access the internet, ping localhost (or 127.0.0.1), lan computers, my router, google.com, etc.

Any tips or suggestions?

Thanks in advanced,
Derek

---

### Post by superprash2003 on 2009-06-11
you cant even ping 127.0.0.1 ?? post output of
1)ifconfig
2)sudo iptables -L
3)route -n

---

### Post by MaindotC on 2009-06-11
Check your syslog and messages for the time that you had a problem.

---

### Post by mrdek11 on 2009-06-11
Odd... I woke up this morning, and went to go get the output of those commands for you, only to find that the network is now working perfectly. I'm not really sure what happened, but it works now.

Thanks everybody!

---

### Post by mrdek11 on 2009-08-12
> **superprash2003 said:**
> you cant even ping 127.0.0.1 ?? post output of
1)ifconfig
2)sudo iptables -L
3)route -n

I've been running into this problem at least once per 3 days. Restarting doesn't help. Connecting with a different cable, different router, and different modem doesn't help.
I can't ping localhost unless the internet works. If I have an IP from the router, and it's listed as "connected", but I can't access the internet, or LAN computers, I can't connect to localhost either.

ifconfig responds:
```
eth0     Link encap:Ethernet HWaddr 00:24:1d:24:76:ce
         inet addr:192.168.0.125 Bcast:192.168.0.255 Mask:255.255.255.0
         inet6 addr: fe0::224:1dff:fe24:76ce/64 Scope:Link
         UP BROADCAST RUNNING MULTICAST  MTU:1500 Metric:1
         RX packets:317 errors:0 dropped:0 overruns:0 frame:0
         TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
         collisions: 0 txqueuelen:1000
         RX bytes:32283 (32.2 KB)  TX bytes:1212 (1.2 KB)
         Interrupt:253 Base address:0x4000

lo       Link encap:Local Loopback
         inet addr:127.0.0.1 Mask:255.0.0.0
         inet6 addr: ::1/128 Scope:Host
         UP LOOPBACK RUNNING MTU:16436 Metric:1
         RX packets:77 errors:0 dropped:0 overruns:0 frame:0
         TX packets:77 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:0
         RX bytes:13582 (13.5 KB)  TX bytes:13582 (13.5 KB)
```

sudo iptables -L responds:
```

Chain INPUT (policy ACCEPT)
target     prot opt source     destination
QUEUE      all  -- anywhere    anywhere

Chain FORWARD (policy ACCEPT)
target     prot opt source     destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source     destination
QUEUE      all -- anywhere     anywhere
```

route -n responds:
```

Kernel IP routing table
Destination   Gateway     Genmask       Flags Metric Ref Use Iface
192.168.0.0   0.0.0.0     255.255.255.0 U     1      0   0   eth0
169.254.0.0   0.0.0.0     255.255.0.0   U     1000   0   0   eth0
0.0.0.0       192.168.0.1 0.0.0.0       UG    0      0   0   eth0

```

---

### Post by Iowan on 2009-08-13
> **mrdek11 said:**
> route -n responds:
```

Kernel IP routing table
Destination   Gateway     Genmask       Flags Metric Ref Use Iface
[COLOR="Red"]192.158.0.0[/COLOR]   0.0.0.0     255.255.255.0 U     1      0   0   eth0
169.254.0.0   0.0.0.0     255.255.0.0   U     1000   0   0   eth0
0.0.0.0       192.168.0.1 0.0.0.0       UG    0      0   0   eth0

```That seems a bit odd...

---

### Post by mrdek11 on 2009-08-13
> **Iowan said:**
> That seems a bit odd...



I have no experience with that command but I thought the same thing.

Oh, whoops! I was posting that from my iphone, and didn't realize you highlighted part of it. That was a typo (I manually copied the text from the other computer). That originally said "192.168.0.0". Sorry!

---

### Post by mrdek11 on 2009-08-13
After doing some more searching, the problem appears to be related to my Realtek 8168 ethernet card. I've followed a bunch of tutorials that supposedly fix it, but none of them have worked. I disabled the r8169 module, and built the latest r8168.
Everybody else seems to have had this problem fixed by getting the other driver.

I've been messing around with settings so much, that I fear I may have now broken something.
On all my other systems, auto eth0 was defined in /etc/network/interfaces. This wasn't so for this machine, so I added:
```
auto eth0
iface eth0 inet dhcp
```
Somehow in the middle of it all, the network connection button has changed. It says ```
Wired Network (grayed)
Auto Ethernet (it's connected to this one)
``` I believe it used to say "Auto eth0".

If I open the network connections dialog, the only "wired" connection listed is "Auto Ethernet". When I open the settings for this connection, the "MAC Address" input box is empty, 802.1x is disabled, and IPv4 Settings is set to "DHCP".

Could it be that my card is simply improperly configured now?

Thanks for all your help,
 Derek

[edit]Rebooted, and that connection "Auto Ethernet" is gone from the connections manager. The panel claims it is disconnected, but eth0 is bound to an IP, and dhclient still works.[/edit]

---

### Post by Iowan on 2009-08-13
Network Manager doesn't touch (or acknowledge?) interfaces defined in */etc/network/interfaces*. Sometimes that's handy (about the only way to activate more than one interface), but sometimes it's annoying to have NM report an "unmanaged" connection.

---

### Post by mrdek11 on 2009-08-13
I just inserted a wifi card, booted up, and it asked for the wifi password. It claims to now be connected to the wifi, I have an IP, etc, but I cannot ping anybody. Not localhost, not my LAN computers, not google.com

This is getting really frustrating. Can anybody please help?

---

### Post by mrdek11 on 2009-08-13
Is there a way to restore the default network settings from the CD? I've probably broken things along the way following the hundreds of tutorials trying to fix this problem, it'd be nice to be able to repair it. I can't reformat because this is a myth box with hundreds of gigabytes of videos and myth was nearly impossible to set up.

---

