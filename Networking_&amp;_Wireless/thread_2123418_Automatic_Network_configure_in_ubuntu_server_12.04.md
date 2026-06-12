---
title: "Automatic Network configure in ubuntu server 12.04.1 ?"
date: 2013-03-07
forum: Networking &amp; Wireless
---

### Post by gauravjain on 2013-03-07
I am having this problem everytime i change NIC or CPU. Ubuntu does not take network configuration automatically.
After a lot effort this time i can access Ubuntu in LAN. But still i can't access internet.

Output of commands i tried :
**ip addr **

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether ec:a8:6b:f0:c6:f9 brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.139/24 brd 192.168.0.255 scope global eth2
    inet6 fe80::eea8:6bff:fef0:c6f9/64 scope link 
       valid_lft forever preferred_lft forever


**dmesg |grep eth**
[    0.743255] i2c-core: driver [aat2870] using legacy suspend method
[    0.743257] i2c-core: driver [aat2870] using legacy resume method
[    1.479450] r8169 0000:02:00.0: eth0: RTL8168evl/8111evl at 0xffffc9000064c000, ec:a8:6b:f0:c6:f9, XID 0c900800 IRQ 43
[    1.479458] r8169 0000:02:00.0: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[   10.789250] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   10.877426] udevd[368]: renamed network interface eth0 to eth2
[ 1061.312562] r8169 0000:02:00.0: eth2: link down
[ 1061.312569] r8169 0000:02:00.0: eth2: link down
[ 1061.312825] ADDRCONF(NETDEV_UP): eth2: link is not ready
[ 1062.878234] r8169 0000:02:00.0: eth2: link up
[ 1062.878613] ADDRCONF(NETDEV_CHANGE): eth2: link becomes ready
[ 1073.140947] eth2: no IPv6 routers present


**dhclient**

Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service smbd reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the reload(8) utility, e.g. reload smbd

**dhclient eth2**
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service smbd reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the reload(8) utility, e.g. reload smbd
RTNETLINK answers: File exists

**/etc/init.d/networking restart**
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                          Cannot find device "eth0"
Failed to bring up eth0.

**ip link**
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether ec:a8:6b:f0:c6:f9 brd ff:ff:ff:ff:ff:ff

**lspci -v** : 02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
	Subsystem: Intel Corporation Device 2042
	Flags: bus master, fast devsel, latency 0, IRQ 43
	I/O ports at e000 [size=256]
	Memory at f0004000 (64-bit, prefetchable) [size=4K]
	Memory at f0000000 (64-bit, prefetchable) [size=16K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Endpoint, MSI 01
	Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
	Capabilities: [d0] Vital Product Data
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Virtual Channel
	Capabilities: [160] Device Serial Number 02-00-00-00-68-4c-e0-00
	Kernel driver in use: r8169
	Kernel modules: r8169

May i change eth2 to eth0 ??? Because i can't change /etc/network/interfaces file. It shows read-only mode. I tried with root in terminal to change , Used gksudo nautilus command , Gedit or nano even cant change. I tried a lot to edit but still can't.
Help me..   
I have to send dhcp request manually for ip right now by using this command:
[B]dhclient eth2
[/B]
But that is for only LAN access. Still cant access internet. Help me to change eth2 to eth0 or i can write in /etc/network/interfaces file (read-only).

---

### Post by papibe on 2013-03-08
Hi  gauravjain.

Could you post the results of these commands?
```
cat /etc/network/interfaces

apt-cache policy network-manager

route -n

nslookup ubuntu.com

dig ubuntuforums.org
```
Regards.

---

### Post by gauravjain on 2013-03-08
> **papibe said:**
> Hi  gauravjain.

Could you post the results of these commands?
```
cat /etc/network/interfaces

apt-cache policy network-manager

route -n

nslookup ubuntu.com

dig ubuntuforums.org
```
Regards.


**cat /etc/network/interfaces**
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet dhcp




**apt-cache policy network-manager**
network-manager:
  Installed: 0.9.4.0-0ubuntu4.1
  Candidate: 0.9.4.0-0ubuntu4.2
  Version table:
     0.9.4.0-0ubuntu4.2 0
        500 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates/main amd64 Packages
 *** 0.9.4.0-0ubuntu4.1 0
        100 /var/lib/dpkg/status
     0.9.4.0-0ubuntu3 0
        500 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise/main amd64 Packages


**route -n**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth2
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth2


**nslookup ubuntu.com**
Server:		192.168.0.1
Address:	192.168.0.1#53


Non-authoritative answer:
Name:	ubuntu.com
Address: 91.189.94.156


**dig ubuntuforums.org**


; <<>> DiG 9.8.1-P1 <<>> ubuntuforums.org
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 36800
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 3, ADDITIONAL: 3


;; QUESTION SECTION:
;ubuntuforums.org.		IN	A


;; ANSWER SECTION:
ubuntuforums.org.	136	IN	A	91.189.94.12


;; AUTHORITY SECTION:
ubuntuforums.org.	102075	IN	NS	ns2.canonical.com.
ubuntuforums.org.	102075	IN	NS	ns3.canonical.com.
ubuntuforums.org.	102075	IN	NS	ns1.canonical.com.


;; ADDITIONAL SECTION:
ns1.canonical.com.	134586	IN	A	91.189.94.173
ns2.canonical.com.	134586	IN	A	91.189.95.3
ns3.canonical.com.	134586	IN	A	209.6.3.210


;; Query time: 1 msec
;; SERVER: 192.168.0.1#53(192.168.0.1)
;; WHEN: Fri Mar  8 11:10:32 2013
;; MSG SIZE  rcvd: 165

---

### Post by papibe on 2013-03-08
Thanks.

You seem to be running the Desktop edition instead of the Server edition.

Since you have installed the network-manager, all network tweaks must be done using the GUI tools ('network connections').

Nevertheless, for what I can see you have an IP assigned on eth2 using DHCP, routes are good, and DNS is working OK.

Why do you say you can't access the Internet? You can't browse? ping? update?

Let us know how it goes.
Regards.

---

### Post by gauravjain on 2013-03-08
No. I could not surf any webpages with web browser. i get this error:

Oops! It was not possible to show this website


The website at [http://ubuntu.com/](http://ubuntu.com/) seems to be unavailable. The precise error was:


Cannot resolve proxy hostname ()


It could be temporarily switched off or moved to a new address. Don't forget to check that your internet connection is working correctly.


Try again

This is might be happens because of interfaces file. Did you see my interfaces file it has configuration for eth0 and lo only, not for eth2. Ip has been assigned on eth2
I can not change interfaces file , i tried lot to change it shows Read-only. 
Is that possible that i can do something so that ip will assign on eth0 ??

---

### Post by papibe on 2013-03-08
It looks like a proxy problem.

Try this:
```
ping -c5 ubuntu.com
```
If that is successful, it means is a problem with your desktop environment, or your browser. 

Desktop: open 'System Settings' and go to 'Network'. Check if there's a proxy set, if so, deactivate it by selecting 'None'.

Browser: (for Firefox) open preferences, go to 'Advanced' and under 'Connection' press 'Settings'. There select either system proxy settings or No proxy.

Let us know how it goes.
Regards.

---

### Post by gauravjain on 2013-03-08
ohhh.. thank you so much sir .. it worked.. i guess the problem i was facing because of proxy. I can access internet now,
But one more thing i want to ask regarding this, 
When i restart ubuntu i have to run this command everytime : dhclient eth2 , To get the IP from the router. Why it doesn't request to router automatically ?

---

### Post by papibe on 2013-03-08
Glad it worked ;)

Since you changed cards, my guess is that NetworkManager is still trying to get a dhcp connection over eth0 instead of the new card (eth2).

Disable eth0:
[LIST]
[*]Open 'Network Connections'.
[*]Go the wired tab, and select eth0.
[*]Press Edit.
[*]In the new Window uncheck the field: 'Connect automatically'.
[/LIST]
Enable eth2:
[LIST]
[*]Open 'Network Connections'.
[*]Go the wired tab, and select eth2.
[*]Press Edit.
[*]In the new Window check the field: 'Connect automatically'.
[*]Then go to the IPv4 settings tab, and make sure the Method is set to 'Automatic (DHCP)'.
[/LIST]

Let us know how it goes.
Regards.

---

### Post by gauravjain on 2013-03-08
Yes you are right sir. Its still trying to connect dhcp over eth0.
But i can't edit eth0 because someone has clicked on connect automatically i think, so it doesn't let me change anything there.
So Is there any way so that i can edit it ?

---

### Post by papibe on 2013-03-09
Let's remove all eth0 references on /etc/network/interfaces.

First, make sure the file it is writeable:
```
sudo chmod 644 /etc/network/interfaces
``` 
Then edit the file:
```
gksudo gedit /etc/network/interfaces
```
Edit it so it looks like this:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
```
Restart your network:
```
sudo service network-manager restart
```
Then try to edit your connections as described on post #8.

Let us know how it goes.
Regards.

---

### Post by gauravjain on 2013-03-11
I have tried to give the write permission to the interfaces file but it gives me following error
 root@gaurav:~# sudo chmod 644 /etc/network/interfaceschmod: changing permissions of `/etc/network/interfaces': Operation not permitted

so that i cant change the file because it is still showing read-only

---

### Post by steeldriver on 2013-03-11
> **gauravjain said:**
> 
 [COLOR=#ff0000]root[/COLOR]@gaurav:~# [COLOR=#ff0000]sudo[/COLOR] chmod 644 /etc/network/interfaceschmod: changing permissions of `/etc/network/interfaces': Operation not permitted


Are you doing this from the recovery console? if so, the filesystem is likely mounted read-only

Also, you don't need sudo if you are already root

---

### Post by gauravjain on 2013-03-11
No.. No.. I am not doing in recovery mode.. I am doing everything in a main os.
And I also tried without sudo. But still getting same error. 
I cant understood anything.

---

### Post by steeldriver on 2013-03-11
OK so maybe you made the file immutable for some reason? you can check with

```
lsattr /etc/network/interfaces
```

If so you will need to use 

```
sudo chattr -i /etc/network/interfaces
```

before you can change the mode - but you should understand WHY you made it immutable

```

$ sudo chmod 600 /etc/network/interfaces
$ ls -l /etc/network/interfaces 
-rw------- 1 root root 116 Feb 20 08:35 /etc/network/interfaces

$ sudo chattr +i /etc/network/interfaces
$ lsattr /etc/network/interfaces 
----i--------e- /etc/network/interfaces

$ sudo chmod 644 /etc/network/interfaces
chmod: changing permissions of `/etc/network/interfaces': Operation not permitted
$
$ sudo chattr -i /etc/network/interfaces
$ sudo chmod 644 /etc/network/interfaces
$ ls -l /etc/network/interfaces 
-rw-r--r-- 1 root root 116 Feb 20 08:35 /etc/network/interfaces

```

---

### Post by gauravjain on 2013-03-12
I don't know how to say you thanx... It worked great... and I removed total eth0 from /etc/network/interfaces. Now it takes IP automatically from router. Thank u so much...

---

