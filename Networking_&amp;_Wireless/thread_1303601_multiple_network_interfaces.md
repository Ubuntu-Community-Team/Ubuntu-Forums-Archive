---
title: "multiple network interfaces"
date: 2009-10-28
forum: Networking &amp; Wireless
---

### Post by bjrnfrdnnd on 2009-10-28
Hi all,

I don't really know how to solve the following problem:
I have a Qnap-Nas with two network interfaces.
One has a fixed IP, and I can connect to the Nas using the usual
network interface with my ubuntu machine.
In order to do so, I write something like

xxx.xxx.xxx.xxx:/Public /mnt/nas/Public nfs rw,users,auto 0 0

in my /etc/fstab file

xxx.xxx.xxx.xxx

is the IP-Address of the NAS.

Now, I want to use a second, faster Connection. The NAS has two network interfaces; I set up the NAS to use both, one as a fixed IP accessible from everywhere, the other as a local IP.

yyy.yyy.yyy.yyy

I have a second Gigabit interface for my Ubuntu box:

ifconfig

//snip//
eth1      Link encap:Ethernet  HWaddr hh:hh:hh:hh:hh:hh
          inet6 addr: fe80::211:3bff:fe0a:a125/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1435 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:145318 (145.3 KB)  TX bytes:2178 (2.1 KB)
          Interrupt:250 Base address:0xc000 
//snip//

I want to access the Public share on the NAS via the fast connection that I just established. What should I write into my 

/etc/fstab and /etc/network/interfaces?

For the moment, I just specified my first interface:

auto eth0
iface eth0 inet static
        address aaa.aaa.aaa.aaa
        netmask 255.255.255.192
        gateway ggg.ggg.ggg.254
	dns-nameservers ddd.ddd.ddd.ddd

Is there a way to establish such a thing using some kind of GUI?

How should I set up the NAS exactly?

Any help appreciated!

---

### Post by bjrnfrdnnd on 2009-10-28
I managed to setup the private network.
My /etc/fstab now looks like this

//snip//
auto eth1
iface eth1 inet static
       address 192.168.1.3
       netmask 255.255.255.0
       #gateway 192.168.1.1
//snip//

I can mount the NAS on the private network without problems.
However, I do not have any internet connection anymore...
I tried to comment out the gateway entry as shown above, but 
that doesn't help.
Any ideas?

---

### Post by bjrnfrdnnd on 2009-10-28
Network just started working with commented gateway line.
Thanks anyways!

---

