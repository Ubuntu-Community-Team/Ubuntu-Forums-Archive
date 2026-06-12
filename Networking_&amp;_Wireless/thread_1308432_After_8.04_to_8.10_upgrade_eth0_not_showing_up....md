---
title: "After 8.04 to 8.10 upgrade eth0 not showing up..."
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by chipyoung on 2009-10-31
Please help.

I have been round and round on this problem.  Everything was working fine in 8.04 until I upgraded to 8.10.  I lost my network connection eth0 after I upgraded.  I tried a 'live CD' of 8.10 and I was able to connect to the network immediately through eth0.

When I do an 'ifconfig' I only get 'lo' and not eth0. I have been to the /etc/network/interfaces file many times using configurations that have worked in the past.  I have looked at dmesg many times and I don't see any problems other than SAMBA not loading correctly, which makes sense.  I am also running 9.04 on a different drive on the same machine with no problems connecting to the internet and the network.

I'll be more than happy to provide any files that would be needed to solve this problem.  My last attempt in the file etc/network/interfaces was this. Which has always worked in the past.

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

I also ran the following commands with these results.

cyoung@Newbox:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 B)  TX bytes:200 


cyoung@Newbox:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:21:85:99:58:5e  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:221 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 B)  TX bytes:200 (200.0 B)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



Thank you in advance,
Chip

---

### Post by Iowan on 2009-10-31
I presume you tried letting NM (Network Manager) handle the DHCP connection? Seems like Hardy and Intrepid were a little touchy.

---

### Post by Iowan on 2009-10-31
I presume you tried letting NM (Network Manager) handle the DHCP connection? Seems like Hardy and Intrepid were a little touchy. 

BTW, what's the **vboxnet0** interface?

---

### Post by chipyoung on 2009-11-01
Iowan,

Thanks for your reply.  You won't believe what happened.  I went to sleep last night and when I woke up I tried my box again and it worked.  The only thing I did last night was to change /etc/network/interfaces to;

auto eth0
iface eth0 inet static
address 192.168.0.195
netmask 255.255.255.0
gateway 192.168.0.1
broadcast 192.168.0.255

instead of dhcp.  Go Figur!

The vboxnet0 is part of my network connection for virtualbox (very slick).

It's funny my network manager applet is still showing no connection.  I think I might deep six it.

Thanks again,
Chip

---

### Post by Iowan on 2009-11-01
> **chipyoung said:**
> It's funny my network manager applet is still showing no connection.  If the interface is configured in */etc/network/interfaces*, NM won't manage it (or... acknowledge it).

---

### Post by chipyoung on 2009-11-01
iowan,

Well after rebooting my machine the same problem came back.  Now no eth0 again...any thoughts?

I am dumbfounded.

Chip

---

### Post by chipyoung on 2009-11-01
After more research I found my problem related to the /var/run/network directory and the file ifstate.  On my working Ubuntu program the directory /var/run/network is created with the file ifstate at bootup the.  Then the directory 'network' is deleted when you reboot Ubuntu, it's then recreated at boot up.  On my problem Ubuntu 8.10 I must delete the file ifstate but keep the sub directory 'network' before rebooting.

Can anyone help me with this?  Which module controls this?

Please HELP

---

### Post by chipyoung on 2009-11-01
Fixed...I upgraded to 9.04.

Thanks for your time and help.

Chip

---

