---
title: "Networking completely borked after reboot"
date: 2010-09-11
forum: Networking &amp; Wireless
---

### Post by Shay Guy on 2010-09-11
I made some updates and rebooted (out of necessity due to an old, mysterious glitch that made my keyboard stop working, along with cursors in text and most menus) and my laptop's networking stopped working altogether. Trying to access my home's wireless network only got me a "disconnected - you are now offline" after a long wait, which has happened before, but A) never before right after a reboot, B) the *wired* connection didn't work either when I tried it, which has *never* happened to me, and C) this persisted after another reboot. I'm out of ideas.

---

### Post by CharlesA on 2010-09-11
Post the output of this please:

```
ifconfig
```

What sort of updates did you install?

---

### Post by Shay Guy on 2010-09-11
All I can remember are some Firefox updates. (That also told me I needed to restart Firefox for them to take effect.)

```
eth0      Link encap:Ethernet  HWaddr 00:1e:68:12:c2:e6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:29 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:1c:bf:78:5b:b0  
          inet6 addr: fe80::21c:bfff:fe78:5bb0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:477 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:41316 (41.3 KB)  TX bytes:12115 (12.1 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:25775 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25775 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3299234 (3.2 MB)  TX bytes:3299234 (3.2 MB)


```

---

### Post by linuxusr50 on 2010-09-12
Try running

```
sudo dhclient
```

from the terminal window.  That should cause you dhcp client to try and get a new ip address.

---

### Post by Shay Guy on 2010-09-12
No effect. If it helps, here's the output:

```
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/vboxnet0/0a:00:27:00:00:00
Sending on   LPF/vboxnet0/0a:00:27:00:00:00
Listening on LPF/eth1/00:1c:bf:78:5b:b0
Sending on   LPF/eth1/00:1c:bf:78:5b:b0
Listening on LPF/eth0/00:1e:68:12:c2:e6
Sending on   LPF/eth0/00:1e:68:12:c2:e6
Sending on   Socket/fallback
DHCPDISCOVER on vboxnet0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on vboxnet0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on vboxnet0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on vboxnet0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on vboxnet0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on vboxnet0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

---

### Post by MaindotC on 2010-09-12
This just happened to me yesterday.  I was playing Counterstrike in Wine at the time, and network-manager just broke.  Couldn't find anything in event logs, couldn't find anything that explained what happened or why.  Usually when something happens, there's some kind of event that triggers like - like a file being deleted, someone maliciously connecting to my machine and executing a command to screw up my network settings beyond comprehension, or even a hardware failure.  I could not "solve" the problem, even after reinstall network-manager.  I had to remove network-manager and just use ifconfig.  I know this doesn't really fix the problem but it is a work around.  Hopefully you can live without the nice nm-applet.

---

### Post by Shay Guy on 2010-09-12
> **strAlan said:**
> I had to remove network-manager and just use ifconfig.  I know this doesn't really fix the problem but it is a work around.

I don't even know how to do *that*. :( One Google and I'm already lost.

---

### Post by CharlesA on 2010-09-12
> **Shay Guy said:**
> I don't even know how to do *that*. :( One Google and I'm already lost.

What you could try is running this from a terminal:

```
sudo apt-get purge network-manager
```

It'll probably spit back an error saying that "[COLOR="Red"]dpkg: warning: while removing network-manager, directory '/var/lib/NetworkManager' not empty so not removed.[/COLOR]"

On my install the only file that was in that directory was NetworkManager.state, which can by removed before reinstalling like so:

```
sudo rm -ri /var/lib/NetworkManager
```

Then reinstall network manager:

```
sudo apt-get install network-manager
```

---

### Post by Shay Guy on 2010-09-12
Reinstallation failed, apparently due -- predictably enough -- to an inability to access the relevant servers. And I'm still confused on how to use ifconfig to connect.

---

### Post by MaindotC on 2010-09-12
If you ever want to know how to use a command there is something called a manpage that documents how it is used:```
man ifconfig
```For the *wired* connection, you can place the following in /etc/network/interfaces and then restart networking - I even listed that command for you as well.```
#First edit the interfaces file
sudo nano /etc/network/interfaces /etc/network/interfaces.bak

#Type the following in it:
iface eth0 inet dhcp

#Press ctrl + x to close the file and save it when prompted
#Use the following command to restart networking:
sudo /etc/init.d/networking restart
```

Your wired interface should request a DHCP lease from your access point and be connected.  For connecting a wireless interface just type:```
man interfaces
```

---

### Post by Shay Guy on 2010-09-12
The ifconfig manpage had been confusing me, but thanks.

Even adding "iface eth0 inet dhcp" *and* "iface eth1 inet dhcp" to the interfaces page and restarting /etc/init.d/networking didn't help.

---

### Post by MaindotC on 2010-09-12
Did you uninstall network-manager?

---

### Post by Shay Guy on 2010-09-12
Yes, yesterday.

---

### Post by MaindotC on 2010-09-12
> **Shay Guy said:**
> Yes, yesterday.

Well unless you have something else controlling your network connection ifconfig should be the only application interfacing with your network settings.  Do you have anything else installed like Wicd?  If not, describe what happens - what happens that is unexpected?  Did you follow the [General Network Troubleshooting Guide](http://ubuntuforums.org/showthread.php?t=25557)?  If so, that guide tells you what you SHOULD see.  Where is the problem?

Are you able to ping your access point?  Is this a name resolution problem?  You need to give us more information to help you.

---

### Post by Shay Guy on 2010-09-12
> **strAlan said:**
> Well unless you have something else controlling your network connection ifconfig should be the only application interfacing with your network settings.  Do you have anything else installed like Wicd?

No clue.

> **strAlan said:**
> If not, describe what happens - what happens that is unexpected?

What, with [FONT="Courier New"]ifconfig[/FONT]? Nothing stands out; the data list doesn't seem to have anything strange on it. Using the "up" and "down" parameters seem to be doing *something*, since they change whether it says "BROADCAST MULTICAST" or "UP BROADCAST MULTICAST". But nothing's happening in terms of actually connecting to networks.

> **strAlan said:**
> Did you follow the [General Network Troubleshooting Guide](http://ubuntuforums.org/showthread.php?t=25557)?  If so, that guide tells you what you SHOULD see.  Where is the problem?

Hmm... well, I don't know how [FONT="Courier New"]bind[/FONT] works. [FONT="Courier New"]/etc/hosts[/FONT] seems normal, though I don't know what it's supposed to look like, but [FONT="Courier New"]/etc/resolv.conf[/FONT] just says, in full:

```
# Generated by NetworkManager
```

> **strAlan said:**
> Are you able to ping your access point?  Is this a name resolution problem?  You need to give us more information to help you.

Sorry. >_< Pinging localhost and 127.0.1.1 works fine. Pinging what I *think* is the access point (it's the IP address I use to reach the router's setup page, at any rate), says "connect: Network is unreachable". Same for pinging 74.125.227.20. [FONT="Courier New"]arp -a[/FONT] does nothing noticeable.

---

### Post by MaindotC on 2010-09-12
What happened when you issued the /etc/init.d/networking restart command?

You will always be able to ping localhost or 127.0.0.1 because that is the very machine you are using.  If that doesn't work then you have some REAL problems.  Not being able to ping the access point is a problem, because if you can't ping it then you can't reach it and thus your traffic cannot go through it.

I gave you a guide.  What is supposed to be in /etc/resolv.conf?  Why do you think it is empty?

Post the output of ifconfig.

---

### Post by Shay Guy on 2010-09-13
With some help from strAlan (okay, a LOT of help), I installed Wicd as a workaround until the problem with network-manager is identified.

---

