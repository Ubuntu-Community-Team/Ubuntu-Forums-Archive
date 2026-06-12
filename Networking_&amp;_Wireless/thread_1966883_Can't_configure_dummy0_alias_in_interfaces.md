---
title: "Can't configure dummy0 alias in interfaces"
date: 2012-04-27
forum: Networking &amp; Wireless
---

### Post by davidknight on 2012-04-27
I want to configure multiple address on the dummy0 interface

I can do this on the command line

/sbin/ifconfig dummy0 192.0.2.1/32
/sbin/ifconfig dummy0:0 192.0.2.2/32

and I get

dummy0    Link encap:Ethernet  HWaddr 5e:b3:58:42:01:7f  
          inet addr:192.0.2.1  Bcast:255.255.255.255  Mask:0.0.0.0
          inet6 addr: fe80::5cb3:58ff:fe42:17f/64 Scope:Link
          UP BROADCAST RUNNING NOARP  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:1890 (1.8 KB)

dummy0:0  Link encap:Ethernet  HWaddr 5e:b3:58:42:01:7f  
          inet addr:192.0.2.2  Bcast:255.255.255.255  Mask:0.0.0.0
          UP BROADCAST RUNNING NOARP  MTU:1500  Metric:1

Hooray!

This doesn't work when I put it into /etc/network/interfaces however

I put this into /etc/network/interfaces

auto dummy0
iface dummy0 inet static
  address 192.0.2.1/32

auto dummy0:0
iface dummy0:0 inet static
  address 192.0.2.2/32

Restart networking

# /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...
ssh stop/waiting
ssh start/running, process 13697
ssh stop/waiting
ssh start/running, process 13743
ssh stop/waiting
ssh start/running, process 13786
   ...done.

but the alias isn't configured, just this

dummy0    Link encap:Ethernet  HWaddr 5e:b3:58:42:01:7f  
          inet addr:192.0.2.1  Bcast:0.0.0.0  Mask:255.255.255.255
          inet6 addr: fe80::5cb3:58ff:fe42:17f/64 Scope:Link
          UP BROADCAST RUNNING NOARP  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:2030 (2.0 KB)

So I have to resort to doing this

auto dummy0
iface dummy0 inet static
  address 199.7.83.42/32
  post-up /sbin/ifconfig dummy0:0 199.7.83.53/32
iface dummy0 inet6 static
  address 2001:500:3::42/128
  post-up /sbin/ifconfig dummy0:0 add 2001:500:3::53/128

Which does what I want.

Is there an incantation in /etc/network/interfaces which would actually work.

( I'm aware that I could tell the module to allow a dummy1 interface and configure that, but I want to do this as an alias on dummy0 because that _does_ work, just not via the configuration file )

Some clue on how to do this greatly appreciated!

Confirmation that this can't work also appreciated, at least then I can stop poking and live with the dirty post-up solution I already have.

Thanks!
dave

---

