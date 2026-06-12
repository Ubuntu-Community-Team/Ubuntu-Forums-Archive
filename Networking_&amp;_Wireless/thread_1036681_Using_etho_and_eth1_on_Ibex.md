---
title: "Using etho and eth1 on Ibex"
date: 2009-01-11
forum: Networking &amp; Wireless
---

### Post by egd on 2009-01-11
My motherboard has two perfectly functional gigabit NICS.  Under Hardy eth0 was configured with a manual IP 192.168.168.2 and enabled network access across my internal network.  eth1 was set to DHCP and received its IP from my broadband router.  Everything worked just fine.

After fresh installing Ibex on the same PC, eth1 still works as described above, however, for the life of me, I cannot get a statically assigned IP working on eth0.  Running ifconfig yields:```
eth0      Link encap:Ethernet  HWaddr 00:1e:8c:44:b5:06  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:1e:8c:44:b3:58  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:8cff:fe44:b358/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5853 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5668 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4967216 (4.9 MB)  TX bytes:996779 (996.7 KB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:936 (936.0 B)  TX bytes:936 (936.0 B)

```However, when looking at network connections, under eth0 IPv4 settings it is clearly set to Manual IP 192.168.168.2 netmask 255.255.255.0 and both Connect automatically and System setting are ticked.

Any ideas...?

---

### Post by pizmooz on 2009-01-11
How are you configuring the settings?
Through the Network Manager GUI or through editing the /etc/network/interfaces?
If you are fairly experienced with networking and it is a wired network, I would 'apt-get remove network-manager' and configure the network scripts by hand.  For me this is easier, as I find that Network Manager does annoying things.

---

### Post by pizmooz on 2009-01-11
OK I see that you are configuring it with the GUI.  And I don't think what is going on is what I thought was going on because you have 0 TX , 0 RX.

What do you get when you:

```

ethtool -i eth0
ethtool -i eth1
lspci | grep -i ethernet

```

---

### Post by Iowan on 2009-01-11
What's in */etc/network/interfaces*? [Here]("http://ubuntuforums.org/showthread.php?t=974382") is a workaround for the NM static address bug. Save the "removing NM" until after you've tried some of the other options... although some would recommend dumping NM for WICD as first option.

---

### Post by egd on 2009-01-12
> **pizmooz said:**
> OK I see that you are configuring it with the GUI.  And I don't think what is going on is what I thought was going on because you have 0 TX , 0 RX.

What do you get when you:

```

ethtool -i eth0
ethtool -i eth1
lspci | grep -i ethernet

```

$ ethtool -i eth0 &&  ethtool -i eth1
driver: sky2
version: 1.22
firmware-version: N/A
bus-info: 0000:02:00.0
driver: skge
version: 1.13
firmware-version: N/A
bus-info: 0000:0a:04.0

---

### Post by egd on 2009-01-12
> **Iowan said:**
> What's in */etc/network/interfaces*?$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

---

### Post by egd on 2009-01-12
It seems this is a known bug in NetworkManager that somehow slipped through the cracks.  WTF, none of the Ubuntu developers use a static IP?

There are a number of workarounds littered on the web, most of which entail removing NetworkManager.  Quite laughable that simplified networking was one of Ibex's much lauded features...doesn't say much for testing. Damnit this is frustrating, I'm beyond wanting to fiddle, I just want stuff to work, especially when it's basic stuff like static IP wired networking, FFS!

Even more laughable is that Ibex has been out since October...it's now mid-Jan and still no bug fix.

---

### Post by dmizer on 2009-01-12
> **Iowan said:**
> [snip]although some would recommend dumping NM for WICD as first option.
Actually, I would strongly advise AGAINST removing NM because it takes the Ubuntu-desktop metapackage with it, which means no more automated updates.

The better way to resolve this is to simply disable NM. That way you can get it back whenever you like.

Make two files which contain nothing but the word: exit

```
echo "exit" | sudo tee -a /etc/default/NetworkManager
echo "exit" | sudo tee -a /etc/default/NetworkManagerDispatcher
```
Reboot, and NM will not work, but remains installed. To re-enable NM, simple remove /etc/default/NetworkManager and /etc/default/NetworkManagerDispatcher.

---

### Post by zika on 2009-01-12
> **dmizer said:**
> Actually, I would strongly advise AGAINST removing NM because it takes the Ubuntu-desktop metapackage with it, which means no more automated updates.

The better way to resolve this is to simply disable NM. That way you can get it back whenever you like.

Make two files which contain nothing but the word: exit

```
echo "exit" | sudo tee -a /etc/default/NetworkManager
echo "exit" | sudo tee -a /etc/default/NetworkManagerDispatcher
```Reboot, and NM will not work, but remains installed. To re-enable NM, simple remove /etc/default/NetworkManager and /etc/default/NetworkManagerDispatcher.

I've done this and NetworkManager is still in the list of all processes. is that OK? I'm not using NM for some time, I've unchecked its entry in Sessions list but it is always sleeping in the process-list. I hoped that this would be the way to get it out. I do not want to uninstall it ...

(I do not have problem with setting static IP, this is just because I've been searching for the way to "kill" NM for sime time now and this is the first time anybody gave the sound proposal ...)

---

### Post by dmizer on 2009-01-12
> **zika said:**
> I've done this and NetworkManager is still in the list of all processes. is that OK?

It should disappear after you reboot. If not, I'll double check with a test Ibex machine I have here.

---

### Post by zika on 2009-01-12
> **dmizer said:**
> It should disappear after you reboot. If not, I'll double check with a test Ibex machine I have here.
it didn't. I did reboot. I'll just try it again.

*after reboot*

here it is, live and kicking ...:

```

$ cat  /etc/default/NetworkManager
exit
$ cat  /etc/default/NetworkManagerDispatcher 
exit
$ ps -e
...
 5773 ?        00:00:00 NetworkManager
 5785 ?        00:00:00 wpa_supplicant
 5790 ?        00:00:00 nm-system-setti
...
$
```

---

### Post by dmizer on 2009-01-12
> **zika said:**
> it didn't. I did reboot. I'll just try it again.

*after reboot*

here it is, live and kicking ...:

```

$ cat  /etc/default/NetworkManager
exit
$ cat  /etc/default/NetworkManagerDispatcher 
exit
$ ps -e
...
 5773 ?        00:00:00 NetworkManager
 5785 ?        00:00:00 wpa_supplicant
 5790 ?        00:00:00 nm-system-setti
...
$
```

Ugh ... mine too. That's a new development. It's after midnight here. I'll take a serious look into this tomorrow.

---

### Post by zika on 2009-01-12
> **dmizer said:**
> Ugh ... mine too. That's a new development. It's after midnight here. I'll take a serious look into this tomorrow.
please go to sleep, it is not important ... thank You ... :)

---

### Post by zika on 2009-01-14
a simple:```
/etc/init.d/NetworkManager stop
killall nm-system-settings
``` in **/etc/rc.local** seems to stop NetworkManager from running.

---

### Post by dmizer on 2009-01-14
I found that a little while ago, but I was hoping for something more permanent. That certainly works though.

---

### Post by zika on 2009-01-14
I'm not proud of this makeshift solution but it works (certainly beats the uninstall of NetworkManager which I hate as a "solution"), as You said.
what do You mean by "permanent"? this survives a reboot ... ;)

---

### Post by egd on 2009-01-14
Ok, after much wasted time (this isn't even an acknowelged bug in Ibex yet WTF???) I have found a partial solution that works and enables two NICs to work together, one static, the other dynamic.

Uninstall NetworkManager:```

sudo apt-get remove network-manager network-manager-gnome
```Edit /etc/networks/interfaces:```
sudo gedit /etc/network/interfaces
```keep the following lines:
auto lo 
iface lo inet loopback

add the following lines (modify as necessary to suit your needs):```
auto eth0
iface eth0 inet static
address 192.168.168.2
netmask 255.255.255.0

auto eth1
iface eth1 inet dhcp

```

restart networking:```
sudo /etc/init.d/networking restart  
```

after doing above, running ifconfig returns:```
~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:8c:44:b5:06  
          inet addr:192.168.168.2  Bcast:192.168.168.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:1e:8c:44:b3:58  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:8cff:fe44:b358/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:97 errors:0 dropped:0 overruns:0 frame:0
          TX packets:169 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14435 (14.4 KB)  TX bytes:23839 (23.8 KB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:634 errors:0 dropped:0 overruns:0 frame:0
          TX packets:634 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:64816 (64.8 KB)  TX bytes:64816 (64.8 KB)
```

However, pinging another device in the 192.168.168.x subnet results in 100% packet loss.  Any ideas what else needs to be changed so that Ibex can find its way to other devices in the subnet?

---

### Post by Iowan on 2009-01-14
> **egd said:**
> However, pinging another device in the 192.168.168.x subnet results in 100% packet loss.  Any ideas what else needs to be changed so that Ibex can find its way to other devices in the subnet?Pinging by address or hostname?  A static address loses the benefit of DNS without some tweaking.

---

### Post by egd on 2009-01-14
> **Iowan said:**
> Pinging by address or hostname?  A static address loses the benefit of DNS without some tweaking.
By IP of course :P

---

### Post by dmizer on 2009-01-14
Everything looks right. Any firewalls in place?

---

### Post by egd on 2009-01-15
> **dmizer said:**
> Everything looks right. Any firewalls in place?None that I'm aware of - I've not installed and/or configured any so unless Ubuntu is doing something I'm not aware of, no.

---

### Post by dmizer on 2009-01-15
> **egd said:**
> However, pinging another device in the 192.168.168.x subnet results in 100% packet loss.  Any ideas what else needs to be changed so that Ibex can find its way to other devices in the subnet?
The other device(s) ... do they have firewalls? Are you using a router or a hub for your subnet? Crossover cable?

---

### Post by egd on 2009-01-15
> **dmizer said:**
> The other device(s) ... do they have firewalls? Are you using a router or a hub for your subnet? Crossover cable?

Other devices have no firewalls - none of the stuff on the static IP subnet is Internet facing and all other devices see one another and can communicate.  Nothing's changed in my network config except installing Ibex.  All of the devices are liked via a gigabit switch, no routers/ hubs in the equation.

---

### Post by dmizer on 2009-01-15
Just to make sure, what is the output of:
```
sudo iptables -L
```

---

### Post by egd on 2009-01-15
> **dmizer said:**
> Just to make sure, what is the output of:
```
sudo iptables -L
```

$ sudo iptables -L
[sudo] password for egd: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

---

### Post by dmizer on 2009-01-15
I don't see anything here which provides any reason why you shouldn't be able to ping between ubuntu and any of the devices on the subnet. Can you do anything at all between the subnet devices and Ubuntu? Log into Ubuntu from one of the other computers on the subnet via ssh for example?

---

### Post by zika on 2009-01-24
> **zika said:**
> I'm not proud of this makeshift solution but it works (certainly beats the uninstall of NetworkManager which I hate as a "solution"), as You said.
what do You mean by "permanent"? this survives a reboot ... ;)

I've stumbled on even better solution (that **dmizer** might like better since it does not get NM even started so there is no need for killing ... :) ):```
*Terminal:*
sudo apt-get install sysv-rc-conf
sudo sysv-rc-conf
**un-check (space) all four of NetworkManager appearances in that table**
```the end ... ;)
once You have installed this nice tool You can also do wonders (if You know what You are doing, which I rarely do) to Your boot time and to Your machine's resources.

---

### Post by egd on 2009-01-31
> **dmizer said:**
> I don't see anything here which provides any reason why you shouldn't be able to ping between ubuntu and any of the devices on the subnet. Can you do anything at all between the subnet devices and Ubuntu? Log into Ubuntu from one of the other computers on the subnet via ssh for example?
nothing, eth0's there but inactive.

---

### Post by dmizer on 2009-01-31
The problem may not be with Ibex. What other device(s) do you have on the 192.168.168 subnet?

---

