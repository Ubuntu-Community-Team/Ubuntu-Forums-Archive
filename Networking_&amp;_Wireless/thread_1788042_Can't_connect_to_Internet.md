---
title: "Can't connect to Internet"
date: 2011-06-22
forum: Networking &amp; Wireless
---

### Post by Bellanchor on 2011-06-22
Hi, everyone, 
My ubuntu(version 10.04) can't connect to internet this morning.
a@a-desktop:ifconfig
eth0      Link encap:Ethernet    HWaddr  00:25:11:4d:ec:d5
UP BROADCAST MULTICAST         MTU:1500        Metric:1
RX packets:0   errors:0   dropped:0   overruns:0   frame:0
TX packets:0   errors:0   dropped:0   overruns:0   carrier:0
collisions:0   txqueuelen:1000
RX bytes:0 ( 0.0 B )   TX bytes:0 ( 0.0 B )
Interrupt:27   Base address:0x4000

eth0:avahi    Link encap: Ethernet     HWaddr  00:25:11:4d:ec:d5
inet addr:169.254.10.8     Bcast;169.254.255.255     Mask:255.255.0.0
UP BROADCAST MULTICAST         MTU:1500    Metric:1
Interrupt:27   Base address:0x4000

Lo    Link  encap: Local Loopback
...

/etc/network/interface   file is:
auto lo
iface lo inet loopback
iface eth0 inet dhcp
auto eth0


And in Windows system, there is no problem.
Any advice would help! Thanks!

---

### Post by Dangertux on 2011-06-22
EDIT:

Try 
sudo /etc/init.d/networking/restart 

see if that helps, also check what's in your /etc/resolv.conf

---

### Post by Bucky Ball on 2011-06-22
> **Dangertux said:**
> EDIT:

Try 
sudo /etc/init.d/networking/restart 



This refers to the directory /restart in  /etc/init.d/networking/. There is no such directory. It should be:

```
sudo /etc/init.d/networking restart 
```... with the gap before 'restart'. This probably won't help a lot if you switched you computer on this morning and it's not working as the networking would already be started. 

;)

---

### Post by Bellanchor on 2011-06-22
> **Dangertux said:**
> EDIT:

Try 
sudo /etc/init.d/networking/restart 

see if that helps, also check what's in your /etc/resolv.conf


I've tried restart, and returns: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval  6
again and again, and followed by:
NO DHCPOFFERS recieved
NO working leases in persistent database - sleeping
ssh stop/waiting
ssh start/running process 2342

In the /etc/resolv.conf   , there're 2 namesevers

---

### Post by Bucky Ball on 2011-06-22
Your gateway mask should be 255.255.255.0. It generally is. Try that.

---

### Post by Bellanchor on 2011-06-22
at first I set :
iface eth0 inet dhcp

and there's no IP address returns after  command 'ifconfig'

and  tried the static IP, but still can't connect to the internet.

---

### Post by Bucky Ball on 2011-06-22
> **Bucky Ball said:**
> Your gateway mask should be 255.255.255.0. It generally is. Try that.

Right click Network icon, edit connections, go to wired connection and change your gateway mask, if there is one there.

Also, a static IP won't work if your router has the DHCP server serving IP addresses. That will create a clash and confuse the issue. If you want to try static IP, set it on the local machine and switch off the DHCP server on the router.

---

### Post by Bellanchor on 2011-06-22
> **Bucky Ball said:**
> Right click Network icon, edit connections, go to wired connection and change your gateway mask, if there is one there.

There is one in the wired connection, but says 'never used' at the Last Used colume. I don't know what this is very clearly.
And following your words, I tried to edit it.
In the IPv4 Settings colomn, set method -> Manual, Add the Address, Netmask, Gateway and DNS servers.
I don't know what I'm doing, so I don't know whether I'm doing right just as you suggest.
Unfortunately,It dose not work still.

---

### Post by Bellanchor on 2011-06-22
when I use static IP address, and restart the /etc/init.d/networking, the message returns:
RTNETLINK answers: No such process
SIOCDELRT: no such process

sometimes when I use code```
route add default gw 172.35.1.1
```, this message returns:
SIOCADDRT: no such process

I'm getting more and more confused.
Anyway, thanks to your help Bucky Ball and Dangertux.
I'll continue looking for the solution tomorrow.

---

### Post by sandman887 on 2011-06-24
Are you able to ping your router? Try to ping yourself and see what happens.

```
ping 127.0.0.1
```

If this doesn't work, try this:

```
ping localhost
```

If you are able to ping yourself, that's good. It means it's probably something simple that needs to be fixed.

Also, if you have tcpdump installed, you can listen for network activity. If you are able to capture some packets on your network, perhaps you can pick up some clues by analyzing them.

You need to be root to run tcpdump. 

```
sudo tcpdump -v
```

Also, run this to see if your computer is recognizing your network interface: 

```
lspci
```

Look through the output it generates and see if you recognize any network device in there.

I'm currently trying to fix a friend's computer that I installed Ubuntu 10.04 on that he took over to his cousin's house. It can go online at his house, but not at his cousin's house. However, I suspect that it's using an ip address that I assigned as a static IP, and NOT using DHCP. I am currently looking into this.

But anyway, I don't feel like this is much help, but hey, I tried! ^_^

---

