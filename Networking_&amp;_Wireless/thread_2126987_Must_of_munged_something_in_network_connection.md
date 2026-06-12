---
title: "Must of munged something in network connection"
date: 2013-03-18
forum: Networking &amp; Wireless
---

### Post by Rocket J Squirrel on 2013-03-18
Ubuntu 12.04 using the LXDE desktop. We have a mixed wired and wireless network here, and I prefer to give wired devices fixed IP addresses. Most of the machines are Windows and assigning fixed IP addresses on them is easy, but I've run into trouble doing so on this 12.04 box.

I edited /etc/network/interfaces to read:
```

auto loiface lo inet loopback


auto eth0
iface eth0 inet static
        address 192.168.1.110
        netmask 255.255.255.0
        gateway 192.168.1.1
        dns-nameservers 8.8.8.8 192.168.1.1



```

And rebooted the machine. The edit seems to have performed the desired function: the IP address is now 192.168.1.110. Ifconfig returns:
```

admin@CCD6:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:20:c5:eb:0e  
          inet addr:192.168.1.110  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:20ff:fec5:eb0e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4548 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2818 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3462392 (3.4 MB)  TX bytes:419965 (419.9 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)



```

But there used to be a little icon on the toolbar in the lower right corner, showing a plugged-in Ethernet connection, it's now gone. Network Connections doesn't show anything under the "Wired" tab. And right-clicking where the little icon used to be brings up:

[x] Enable Network
Connection Information
Edit Connections

"Connection Information" says "no valid active connections found"

AND YET I am presently connected to the Internet else I could not send this. 

So clearly I've done a Bad Thing. Thoughts?

---

### Post by Iowan on 2013-03-18
I've been away from the networking side for awhile. At least a few versions ago, Network Manager would not touch interfaces configured via /etc/network/interfaces. The interface still got configured, but NM played dumb. There *should* be an option to make NM deal w/ the interface.
Another option: You should be able to set a fixed address via Network Manager.

I presume it's a typo that > auto lo
iface lo inet loopback
became > auto loiface lo inet loopback

---

### Post by Bucky Ball on 2013-03-18
Yep, Edit Connections and do it via Network Manager.

---

### Post by Rocket J Squirrel on 2013-03-18
> Yep, Edit Connections and do it via Network Manager.

B-but, Edit Connections displays the same screen as Network Manager: Neither show anything under the "Wired" tab.

> [COLOR=#000000]I presume it's a typo that[/COLOR][COLOR=#000000][I]auto lo
iface lo inet loopback
[/I]
[/COLOR]
[COLOR=#000000]became
[/COLOR][COLOR=#000000]*auto loiface lo inet loopback*[/COLOR]

Yup. When I paste things between the CODE tags, they often display (after submitting) with lf/cr's missing.

---

### Post by steeldriver on 2013-03-18
If you define an interface via /etc/network/interfaces, then it will disappear from the network manager applet - they are separate services, and the network-manager service is configured by default to ignore interfaces from the networking service ('[ifupdown] managed=false')

---

### Post by Rocket J Squirrel on 2013-03-18
Steeldriver -- thanks for that explanation. 

Question: if a fellow wants to assign a static IP address, is there a way to do that in a way that doesn't cause NM to go "hands off"?

---

### Post by steeldriver on 2013-03-18
Yes - just go to Edit Connections... on the main menu --> select the connection you want the static address for (Wired or Wireless) --> Edit --> IPv4 Settings tab and change the drop down from Automatic (DHCP) to Manual - then add the desired static IP (and other info such as DNS if appropriate)

---

### Post by Rocket J Squirrel on 2013-03-18
> [COLOR=#000000]Yes - just go to Edit Connections... on the main menu --> select the connection you want the static address for (Wired or Wireless) --> Edit --> IPv4 Settings tab and change the drop down from Automatic (DHCP) to Manual - then add the desired static IP (and other info such as DNS if appropriate)[/COLOR]

Seriously? I don't know why I didn't consider that right away. I just Googled around and found various hand-edits for [COLOR=#000000]/etc/network/interfaces [/COLOR]to force a static IP. 

Shoot. Okay, now that Network Manager no longer wants to have anything to do with managing the network, because I hand-edited [COLOR=#000000]/etc/network/interfaces, how do I get NM to forgive me and be willing to play again?

How about just returning it to its original condition, reading
[/COLOR]```
auto lo
iface lo inet loopback

```

---

### Post by steeldriver on 2013-03-18
yes that should do it - you may need to restart the service(s) after reverting the file

```

sudo service networking restart
sudo service network-manager restart

```

(or just reboot)

---

### Post by Bucky Ball on 2013-03-18
> **steeldriver said:**
> Yes - just go to Edit Connections... on the main menu --> select the connection you want the static address for (Wired or Wireless) --> Edit --> IPv4 Settings tab and change the drop down from Automatic (DHCP) to Manual - then add the desired static IP (and other info such as DNS if appropriate)

Exactly.

---

### Post by Rocket J Squirrel on 2013-03-19
steeldriver, thank you. But
```

admin@CCD6:~$ sudo service networking restart
[sudo] password for admin: 
stop: Unknown instance: 
networking stop/waiting
admin@CCD6:~$ 

```
Still,
```

admin@CCD6:~$ sudo service network-manager restart
network-manager stop/waiting
network-manager start/running, process 12213
admin@CCD6:~$ 

```
And Network Manager reappears. I began editing the Wired Connection to make it Manual, while during so, the computer glitched and a popup informing me that Ubuntu 12.04 suffered an Internal Error. I pressed "continue" and finished the edit, and saved it. I'm going to do a reboot now, see you on the farside.

---

### Post by Rocket J Squirrel on 2013-03-19
... and I'm back and IT'S ALIVE!

Many thanks to all for helping me repair this fumble. Great community here.

---

### Post by Bucky Ball on 2013-03-19
As the regular method of marking threads 'Solved' is broken, please edit the first post, Go Advanced and change the title prefix to Solved. Thanks. 

PS: If you know how you fixed this please share. Did you just reboot after the internal error and everything was fine?

---

### Post by Rocket J Squirrel on 2013-03-19
> [COLOR=#000000]As the regular method of marking threads 'Solved' is broken, please edit the first post, Go Advanced and change the title prefix to Solved. Thanks.[/COLOR]

Aye, will do. 

> [COLOR=#000000]PS: If you know how you fixed this please share. Did you just reboot after the internal error and everything was fine?[/COLOR]

Other than the first command (sudo service networking restart) not returning Good News, everything worked fine. 

Network Manager is back; and today I needed to change the fixed IP address again to eliminate a conflict and Edit Connections in Network Manager followed by "sudo service network-manager restart" worked as advertised.

---

### Post by steeldriver on 2013-03-19
^^^ the 'unknown instance' response from the service networking restart is normal I think - it just means that since you have nothing (apart from the loopback interface) defined in the file, the service wasn't actually started

---

