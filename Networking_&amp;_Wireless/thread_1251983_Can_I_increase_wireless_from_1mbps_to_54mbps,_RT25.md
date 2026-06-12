---
title: "Can I increase wireless from 1mbps to 54mbps, RT2500pci"
date: 2009-08-28
forum: Networking &amp; Wireless
---

### Post by potatan on 2009-08-28
Hi,

I have a homebuilt PC with an RT2500 PCI wireless card running Jaunty with all updates.  I normally use a wired connection but am trying to get wireless working quickly enough to do without the wires.

I have no problem connecting wirelessly, the router is in the same room as the PC and the signal strength hovers around 80%.  But it seems very slow.  Connection information from Network manager applet reports that the connection bitrate is 1 Mb/s, but the router and card are 802.11G.

Is there a way I can tell the card to use the full 54Mbps (minus overheads, obviously), rather than limiting the connection to 1Mbps?

Some command outputs:

```
lspci:

00:0e.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
	Subsystem: ASUSTeK Computer Inc. Device 130f
	Flags: bus master, slow devsel, latency 64, IRQ 19
	Memory at f9c00000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: rt2500pci
	Kernel modules: rt2500pci

lshw -C network:

*-network:1
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: e
       bus info: pci@0000:00:0e.0
       logical name: wmaster0
       version: 01
       serial: 00:11:2f:6e:6f:4e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci ip=192.168.1.64 latency=64 module=rt2500pci multicast=yes wireless=IEEE 802.11bg

ifconfig wlan0:

wlan0     Link encap:Ethernet  HWaddr 00:11:2f:6e:6f:4e  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:2fff:fe6e:6f4e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1367 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1175 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1248770 (1.2 MB)  TX bytes:176229 (176.2 KB)


```

Please let me know if you need more diag info.

Many thanks in advance.

---

### Post by kerry_s on 2009-08-28
it's normal for it to go up & down that's what the "auto" setting does, it uses the rate that is strongest.
the command to set it to a set rate: **sudo iwconfig wlan0 rate 54M**

---

### Post by potatan on 2009-08-28
Thanks, that's great - it's gone from 1 to 54, and my speedtest.net results have gone from about 0.9 up to about 11Mbps.

However, I just rebooted and it was back at 1Mbps (the wireless connection, not speedtest) - how can I make this change permanent?

Many thanks

---

### Post by kerry_s on 2009-08-28
i think thats the mtu setting in the edit connections.

---

### Post by PatrickVogeli on 2009-08-28
add iwconfig wlan0 rate 54M into /etc/rc.local before the exit line

---

### Post by kerry_s on 2009-08-28
> **PatrickVogeli said:**
> add iwconfig wlan0 rate 54M into /etc/rc.local before the exit line

will that work? network manager doesn't bring up the connection till the desktop?

i'm thinking you set it in rc.local, but once the network manager starts it will override that. :confused:

---

### Post by kerry_s on 2009-08-28
alright, i just tested it. you can use rc.local to bring up the connection before you even reach the desktop, just use the command line commands.
add "&" on the end so it don't slow your boot.

i did this in mine:

---

### Post by potatan on 2009-08-31
You're both right - I think!

I added it to rc.local, and sometimes it comes up as 54M and other times as 1M, so I think network manager must be jumping in before rc.local finishes executing, or after, depending on who knows what else?

Any other ideas for making it permanent?

cheers

---

### Post by potatan on 2009-09-02
bump

---

### Post by kerry_s on 2009-09-02
the only thing i can think of is to nopassword iwconfig, then you can run the command in your session startup.

[B]sudo visudo
your-name ALL=NOPASSWD: /usr/sbin/iwconfig
[/B]

for the session startup you need to create the script, cause the session-manager is picky about running full commands.
i'll put the terminal command in "()".

create a ~/.bin folder to hold your script, you can right click-> new folder. (mkdir ~/.bin)

inside ~/.bin right click-> new file (touch ~/.bin/wireless)

in it put:
[B]#!/bin/sh
sudo iwconfig wlan0 rate 54M[/B]

now make it executable, right click the file-> properties-> permission
(chmod +x ~/.bin/wireless)

now just add "wireless" to your session startup using the add button.

then log out & back in & check

---

### Post by potatan on 2009-09-03
Thanks for that.  I've been working around by creating a panel icon with 
```
gksudo iwconfig wlan0 rate 54M
```
for those times when it comes up as 1M, but of course I need to put the password in then.  If I read it correctly, your solution allows me to run iwconfig without a password.

I've added the bash script to startup and will see how it goes over the next few reboots.  Incidentally, this morning's boot produced a 54M connection (before I made these changes), showing how intermittent it is.

On a side note, it's a little frustrating that there's not an easier way to accomplish this.  I take the point about the adaptive connection rate - my laptop drops to about 24 or 36M when I'm a couple of rooms away from the router for instance.  But I don't really think that a 1M connection at startup is all that can be achieved by this PC in the same room as the router, and it will then stay at that rate until I use iwconfig to put it up to 54M.

It'd be nice if the connection would just stick to trying 54M at startup.  Mind you, the wireless PCI card is probably around 5 years old so maybe newer hardware behaves differently.

Cheers

---

### Post by kerry_s on 2009-09-03
the 1M is like a power saving feature, mine drops to 1M when the network is not very active. i notice mine uses 11,23,36, etc... during peak hours when theres a lot of wifi traffic.

---

### Post by potatan on 2009-09-04
Done a bit more testing - the laptop starts up at 54M every time (at least when it's in the same room), yet the desktop (this machine with the RT2500PCI card) almost always starts at 1M, despite all the measures I've taken following the collective advice in this thread.

Maybe Karmic will fix it, but for now, I'll just have to keep clicking my panel icon to set it to 54M, when it starts up at a lower speed.  It's not about congestion, mine is the only wireless PC in the house, apart from the laptop - and I tend not to use them both at the same time, not enough fingers you see!

---

### Post by RavanH on 2009-09-05
Hi potatan,

I had the same issue as you and I got around it by switching from Network Manager to Wicd and adding a little pre-connection script. Wicd is actually working pretty well (I prefer it to NM) and if you get version 1.6+ it is even better.

I wrote a how-to on [http://ubuntuforums.org/showthread.php?p=7605785](http://ubuntuforums.org/showthread.php?p=7605785)

Hope that give you a stable working solution, as it did for me :)

Allard

---

### Post by potatan on 2009-09-07
> **RavanH said:**
> 

Hope that give you a stable working solution, as it did for me :)

Allard

Thanks Allard, just swapped out NM for wicd, as per your instructions, and everything seems to be working well.  I'll know in a few days whether it always comes up at 54M, but it's looking good so far, after a couple of reboots.

I ran into a small problem with your how-to, the wicd downloads site was down, but I managed to get the latest 1.6.2 release by adding the wicd repository to Synaptic package manager, and upgrading from there.

Thanks again!

---

### Post by RavanH on 2009-09-14
glad it worked out for you too and thanks for pointing out the dead link and the fact that the wicd repo is back :)

---

