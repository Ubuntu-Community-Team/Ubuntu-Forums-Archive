---
title: "Samba problem with bridge interface"
date: 2010-09-17
forum: Networking &amp; Wireless
---

### Post by Trixymoon on 2010-09-17
Hi all, 

I have two network interfaces in my pc eth0 and wlan0 and a virtual one br0.

router <= eth0 (0.0.0.0) => br0 (192.168.1.10) <= wlan0 (0.0.0.0) =>  other pc.

On startup of my pc (ubuntu 10.04 server x64), samba bind itself only to loopback network interface, as i can see when i do netstat -an , preventing me to enter in my shares from a remote pc.

Here is my configuration regarding samba network:

```

interfaces = 127.0.0.0/8 192.168.1.0/24
bind interfaces only = yes

```and my /etc/network/interfaces

```

# The loopback network interface
auto lo
iface lo inet loopback

iface eth0 inet manual

iface wlan0 inet manual

auto br0
iface br0 inet static
       bridge_ports eth0 wlan0
        address 192.168.1.10
        network 192.168.1.0
        netmask 255.255.255.0
        gateway 192.168.1.1
        broadcast 192.168.1.255

```If later I run service smbd restart, samba bind itself correctly:

```

tcp        0      0 127.0.0.1:139           0.0.0.0:*               LISTEN     
tcp        0      0 192.168.1.10:139        0.0.0.0:*               LISTEN   
...
tcp        0      0 127.0.0.1:445           0.0.0.0:*               LISTEN     
tcp        0      0 192.168.1.10:445        0.0.0.0:*               LISTEN 

```I think that, during startup upstart loads samba  faster than the bridge configuration, and samba bind itself only on looback address.

I have made some other test with no luck:
I changed the line "interfaces = 127.0.0.0/8 192.168.1.0/24"
to "interfaces = 127.0.0.0/8 192.168.1.0/24 br0"
and rebooted.

Now in my /var/log/samba/log.smbd shows up these lines:
```

[2010/09/17 08:39:56,  0] lib/util_sock.c:938(open_socket_in)
  bind failed on port 445 socket_addr = fe80::201:2eff:fe2f:d55%br0.
  Error = Cannot assign requested address
[2010/09/17 08:39:56,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Cannot assign requested address
[2010/09/17 08:39:56,  0] lib/util_sock.c:938(open_socket_in)
  bind failed on port 139 socket_addr = fe80::201:2eff:fe2f:d55%br0.
  Error = Cannot assign requested address
[2010/09/17 08:39:56,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Cannot assign requested address

```Any idea fo speed up my bridge configuration or to force samba to wait unitl the bridge is ready?
Thanks in advance and sorry for my bad english!

---

### Post by Trixymoon on 2010-09-17
I think i found a solution, not too dirty, to the problem:

sudo nano /etc/init/smbd.conf

and change the line:

start on local-filesystems

to

start on (local-filesystems and net-device-up IFACE=br0)

Now upstart will wait for bridge interface to be up before to start samba.

bye

---

### Post by braincookie on 2012-01-20
I had a similar problem, but I just have a standard eth0 interface (no bridge). For me, the issue was solved by simply changing the bind interfaces in /etc/samba/smb.conf
```

bind interfaces only = no

```(I'm behind a firewall, so no problem with binding to all interfaces)

---

### Post by Trixymoon on 2012-01-20
Thanks for your contribution, however there are several issues of "race condition" that arise when you configure a bridge interface.
See this link here on lunchpad:[ init.d controlled services launch before all interfaces are up, thus failing to start]("https://bugs.launchpad.net/ubuntu/maverick/+source/dhcp3/+bug/580319")

---

