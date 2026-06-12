---
title: "No internet connection after MAC Address changed by Icecast server installation"
date: 2011-02-25
forum: Networking &amp; Wireless
---

### Post by Angel_Caido on 2011-02-25
I have Dual Boot on my PC: LMDE 64 bits on one partition and Ubuntu Lucid Lynx 64 bits in the other one.
I installed icecast server on my LMDE 64 bits to run some testings using that broadcasting software and at a certain point I received the message that the installation process was going to change the MAC address of my netcard to match it up with... something else [i can't recall]. I allowed it. When I rebooted my internet was one, couldn't access it even though the netcard was still recognized. I then Rebooted into Ubuntu and the same happened. I went back to LMDE and disabled the connection for a moment and turned my cable modem off for a few seconds [I don't use a router]; then I turned my cable modem on, waited for all LED to come on and then enabled my netcard and then I got my internet back... on LMDE.
Problem is if I go back to Ubuntu, or even if I boot off of a Live CD on this computer I don't have access to the internet. Before the unfortunate MAC address change I was able to.
Is there anyway I can change the MAC address for my netcard back  to default? Any ideas?
The netcard is a built-in Atheros Communications AR8121/AR8113/AR8114 Gigabit or Fast Ethernet (rev b0) [according to lspci].

The result for **ifconfig -a** is:
```
eth1      Link encap:Ethernet  HWaddr aa:00:04:00:0a:04  
          inet addr:<mi ip adress.xxx.xxx.xxx>  Bcast:69.22.55.168  Mask:255.255.240.0
          inet6 addr: fe80::a800:4ff:fe00:a04/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16532 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2211 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:2975972 (2.8 MiB)  TX bytes:345040 (336.9 KiB)
          Interrupt:29 

```

Thanks.

---

### Post by Angel_Caido on 2011-02-27
Solved.
I Found a workaround [here]("http://debianletters.blogspot.com/2007/12/how-to-change-mac-address-of-ethernet.html").
A little copy/paste:
> 
[B][COLOR="Red"]Temporary MAC-address change
[/COLOR][/B]Go to the terminal and type:
```
sudo ifconfig eth0 hw ether xx:xx:xx:xx

```and MAC-address change and will stay until reboot. If you wish to change MAC-address permanently, you need to do this:


[COLOR="red"][B]Permanent change of MAC-address
[/B][/COLOR]In Debian, for example, go to  **/etc/network/if-pre-up.d/** and create file from root named pre-up.
Let`s write to them strings like this:
```
#! /bin/sh
ifconfig eth0 hw ether 00:00:00:00
```
Change zeroes by needed MAC-address. To make changes active immediately, restart of network subsystem is required:
```
/etc/init.d/networking restart
```
In first time, following diagnostic messages are expected to appear:
```
# /etc/init.d/networking restart
Setting up IP spoofing protection: rp_filter.
Reconfiguring network interfaces...SIOCDELRT: No such process
ifup: interface lo already configured
SIOCSIFHWADDR: Device or resource busy
run-parts: /etc/network/if-pre-up.d/pre-up exited with return code 1
done.
```
No problems, repeat command, and it will execute smoother:
```
notebeast:/home/beast# /etc/init.d/networking restart
Setting up IP spoofing protection: rp_filter.
Reconfiguring network interfaces...ifup: interface lo already configured
done.
```
Here we go, the MAC-address is changed permanently.


[B][COLOR="red"]How to find out MAC-address of network card in Linux
[/COLOR][/B]It's very simple, just type:
```
sudo ifconfig
```
and you see something like this:
```
eth0 Link encap:Ethernet HWaddr 00:0A:E4:53:AA:2D 
inet addr:10.26.49.77 Bcast:10.26.63.255 Mask:255.255.240.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:208554 errors:0 dropped:0 overruns:0 frame:0
TX packets:125071 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:40664531 (38.7 MiB) TX bytes:45919980 (43.7 MiB)
Interrupt:21 Base address:0x4c00 

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:18511 errors:0 dropped:0 overruns:0 frame:0
TX packets:18511 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:537155 (524.5 KiB) TX bytes:537155 (524.5 KiB)

```
One's MAC-address is emphased by red font colour.


Yet another tips to change MAC-address
For example, MAC-address in Gentoo can be changed in **/etc/conf.d/net**


```
mac_eth0="00:50:8D:63:41:DE"
config_eth0=( "192.168.100.37 netmask 255.255.252.0" )
routes_eth0=(
"default via 192.168.100.1"
)
```

Or edit **/etc/network/interfaces** adding one string:
```
pre-up ifconfig eth0 hw ether 00:00:00:00:00:00
```
Indeed, there are loads of variants, because it is Linux :-)
```
iface eth0 inet static
address 192.168.1.1
netmask 255.255.255.0
hwaddress ether xxxxxxxxxxxx
```


---

