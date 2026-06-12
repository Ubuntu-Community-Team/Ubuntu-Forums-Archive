---
title: "Network Manager refuses to detect  network"
date: 2011-07-02
forum: Networking &amp; Wireless
---

### Post by XxionxX on 2011-07-02
Edit: Solved Using: ```
sudo ifup eth0
```Ubuntu 10.04 LTS, Pentium (R) dual core, 1GB memory
 
OK I give up. My Network Manager hates me. :cry: 

Several days ago NM decided to stop working for whatever reason (wired connection). I tried troubleshooting today, and after 3hrs I call uncle.

So far I have tried:

```
sudo nm-applet
```already running...

```
sudo service network-manager stop
``````
rm /var/lib/NetworkManager/NetworkManager.state
``````
sudo service network-manager start
```Restart. Nothing...

```
sudo restart network-manager
```Nothing...

```
gksudo gedit /etc/network/interfaces
```auto lo
iface lo inet loopback

(according to my searches that is correct)


ARGH! Why is this so hard!? I can't even download/install wicd so I can try that! What in the world is going on?

---

### Post by Iowan on 2011-07-02
You can try adding a Notification Area to the top panel - that's where NM is *supposed* to live.

---

### Post by MaindotC on 2011-07-03
> **XxionxX said:**
> Ubuntu 10.04 LTS, Pentium (R) dual core, 1GB memory
 
OK I give up. My Network Manager hates me. :cry: 

Several days ago NM decided to stop working for whatever reason (wired connection). I tried troubleshooting today, and after 3hrs I call uncle.



I had the exact same thing [happen to me.](http://ubuntuforums.org/showthread.php?t=1573766) It's a very difficult issue to troubleshoot because apparently it's not very frequent - otherwise there would be more attention to it.  I cannot advise you how to **resolve** the problem, but I can advise of a workaround.  Remove Network Manager via Synaptic, configure your network manually with /etc/network/interfaces, and install Wicd.  That's the best I can offer for you.

---

### Post by XxionxX on 2011-07-04
> **MaindotC said:**
> I had the exact same thing [happen to me.]("http://ubuntuforums.org/showthread.php?t=1573766") It's a very difficult issue to troubleshoot because apparently it's not very frequent - otherwise there would be more attention to it.  I cannot advise you how to **resolve** the problem, but I can advise of a workaround.  Remove Network Manager via Synaptic, configure your network manually with /etc/network/interfaces, and install Wicd.  That's the best I can offer for you.

Configure manually! :( I never had this problem with 8.10 Aren't things supposed to get better with each new version (lolz)? But really, this sounds like a drag. The box in question is my mother's and she will not be able to troubleshoot in that manner if something goes wrong. I will do it if I have to, but she needs that little icon.

Anyway, how would you go about configuring /etc/network/interfaces? I don't know what to search for to get the right settings/code. I have other computers connected to the network if I need their info (ifconfig etc.).

@Iowan:
NM is open and running, just not working. It keeps refreshing like it is going to connect, and then doesn't. ](*,)

---

### Post by MaindotC on 2011-07-04
> **XxionxX said:**
> Configure manually! :( I never had this problem with 8.10 Aren't things supposed to get better with each new version (lolz)? But really, this sounds like a drag. The box in question is my mother's and she will not be able to troubleshoot in that manner if something goes wrong. I will do it if I have to, but she needs that little icon.

Wicd has an icon...

> Anyway, how would you go about configuring /etc/network/interfaces? I don't know what to search for to get the right settings/code. I have other computers connected to the network if I need their info (ifconfig etc.).

There are millions of guides but you can use the one from [10.04](https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html).  If you're connected to an access point I would just run **sudo dhclient <device_name>** and get it over with.

---

### Post by woodsyboredom on 2011-07-07
Same thing happened to me. i got the notification area back but the network manager applet is just plain gone.

---

### Post by XxionxX on 2011-07-10
MaindotC thanks for the help!

Ok I tried:

```
sudo dhclient  eth0
```

and got

```

~$ sudo dhclient  eth0
There is already a pid file /var/run/dhclient.pid with pid 2005
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/{MAC address edited}
Sending on   LPF/eth0/{MAC address edited}
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

So then I tried the link you sent me. I tried this first:

```
ip addr flush eth0[CODE]

and when I went to /etc/resolv.conf it was blank. -_-

ok...

Then I tried this:

I went to the /etc/network/interfaces file and edited it to look like this:

[CODE]auto eth0
iface eth0 inet dhcp

```

and then ran this

```
sudo ifup eth0
```

I got this

```

~$ sudo ifup eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 3801
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/{MAC address edited}
Sending on   LPF/eth0/{MAC address edited}
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
 * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...fail!
run-parts: /etc/network/if-up.d/50firestarter exited with return code 2
```

-_-    ok....

I tried 

```
sudo ifdown eth0
```

and got

```

~$ sudo ifdown eth0
 * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...fail!
run-parts: /etc/network/if-down.d/50firestarter exited with return code 2
RTNETLINK answers: No such process
SIOCDELRT: No such process
```

I tried the manual configuration of /etc/network/interfaces and tried this:

```
auto eth0
iface eth0 inet static
address 192.168.1.122
netmask 255.255.255.0
gateway 192.168.1.1

```
(All proper settings unless I am being dumb somewhere)

Same deal as before. :(](*,)

I feel like I am missing some crucial knowledge about this problem. Is there a way I can download Wcid on a usb and just bring it over that way?

---

### Post by XxionxX on 2011-07-13
bump :)

---

### Post by DAB4970 on 2011-07-15
Edit the eth0 IP settings manually (static IP address).  It worked for my 64-bit 10.04 and 11.04.  You may have to edit settings on your router for the static IP address.
Something's not right with the DHCP in Network Manager (vs 0.8).

Oh, There's a kernel update to 2.6.32-33.  Wonder if that will help the issue?  We'll see.

After kernel update: It didn't help DHCP issue.

There's a cmd line entry for getting the notification icon back in operation, but I can't remember what it is.  I'll try to look it up and repost it.

Try this to get update notifier working again:  gconftool -s --type bool /apps/update-notifier/auto_launch false

---

### Post by XxionxX on 2011-09-10
So I finally had time to go over to my mothers house (school and work getting in the way). And when I sat down I decided to give ```
sudo ifup eth0
``` a try again on the offhand chance that it would work. It worked. I don't know what had changed, other than the computer had been off for a long time. The network manager still won't come up, but I am through with that stupid thing. So I promptly installed Wcid the normal way now that my Internet was up and I haven't had any problems since.

Thanks for your help everyone! I am glad there is a cool community here to help out with this stuff :D

---

