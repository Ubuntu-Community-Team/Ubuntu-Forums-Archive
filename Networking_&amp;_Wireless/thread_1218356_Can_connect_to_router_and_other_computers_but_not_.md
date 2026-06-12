---
title: "Can connect to router and other computers but not internet"
date: 2009-07-20
forum: Networking &amp; Wireless
---

### Post by crye on 2009-07-20
I was going to install a VNC server onto my Ubuntu Server and it didn't work. So I went to update the server, that didn't work either. It failed to connect to the website to get updates.

```
usaconnect@ubuntu:~$ sudo apt-get update
Err http://security.ubuntu.com hardy-security Release.gpg
  Cannot initiate the connection to security.ubuntu.com:80 (91.189.88.37). - connect (101 Network is unreachable)
Err http://security.ubuntu.com hardy-security/main Translation-en_US
  Cannot initiate the connection to security.ubuntu.com:80 (91.189.88.37). - connect (101 Network is unreachable)
Err http://security.ubuntu.com hardy-security/restricted Translation-en_US
  Cannot initiate the connection to security.ubuntu.com:80 (91.189.88.37). - connect (101 Network is unreachable)
Err http://security.ubuntu.com hardy-security/universe Translation-en_US
  Cannot initiate the connection to security.ubuntu.com:80 (91.189.88.37). - connect (101 Network is unreachable)
Err http://security.ubuntu.com hardy-security/multiverse Translation-en_US
  Cannot initiate the connection to security.ubuntu.com:80 (91.189.88.37). - connect (101 Network is unreachable)
Ign http://security.ubuntu.com hardy-security Release
Ign http://security.ubuntu.com hardy-security/main Packages
Ign http://security.ubuntu.com hardy-security/restricted Packages
Ign http://security.ubuntu.com hardy-security/main Sources
Ign http://security.ubuntu.com hardy-security/restricted Sources
Ign http://security.ubuntu.com hardy-security/universe Packages
Ign http://security.ubuntu.com hardy-security/universe Sources
Ign http://security.ubuntu.com hardy-security/multiverse Packages
Ign http://security.ubuntu.com hardy-security/multiverse Sources
Err http://security.ubuntu.com hardy-security/main Packages
  Cannot initiate the connection to security.ubuntu.com:80 (91.189.88.37). - connect (101 Network is unreachable)
Err http://security.ubuntu.com hardy-security/restricted Packages
  Cannot initiate the connection to security.ubuntu.com:80 (91.189.88.37). - connect (101 Network is unreachable)
Err http://security.ubuntu.com hardy-security/main Sources
  Cannot initiate the connection to security.ubuntu.com:80 (91.189.88.37). - connect (101 Network is unreachable)
Err http://security.ubuntu.com hardy-security/restricted Sources
  Cannot initiate the connection to security.ubuntu.com:80 (91.189.88.37). - connect (101 Network is unreachable)
Err http://security.ubuntu.com hardy-security/universe Packages
  Cannot initiate the connection to security.ubuntu.com:80 (91.189.88.37). - connect (101 Network is unreachable)
Err http://security.ubuntu.com hardy-security/universe Sources
  Cannot initiate the connection to security.ubuntu.com:80 (91.189.88.37). - connect (101 Network is unreachable)
Err http://security.ubuntu.com hardy-security/multiverse Packages
  Cannot initiate the connection to security.ubuntu.com:80 (91.189.88.37). - connect (101 Network is unreachable)
Err http://security.ubuntu.com hardy-security/multiverse Sources
  Cannot initiate the connection to security.ubuntu.com:80 (91.189.88.37). - connect (101 Network is unreachable)
Err http://us.archive.ubuntu.com hardy Release.gpg
  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy/main Translation-en_US
  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy/restricted Translation-en_US
  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy/universe Translation-en_US
  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy/multiverse Translation-en_US
  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy-updates Release.gpg
  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]
Ign http://us.archive.ubuntu.com hardy Release
Ign http://us.archive.ubuntu.com hardy-updates Release
Ign http://us.archive.ubuntu.com hardy/main Packages
Ign http://us.archive.ubuntu.com hardy/restricted Packages
Ign http://us.archive.ubuntu.com hardy/main Sources
Ign http://us.archive.ubuntu.com hardy/restricted Sources
Ign http://us.archive.ubuntu.com hardy/universe Packages
Ign http://us.archive.ubuntu.com hardy/universe Sources
Ign http://us.archive.ubuntu.com hardy/multiverse Packages
Ign http://us.archive.ubuntu.com hardy/multiverse Sources
Ign http://us.archive.ubuntu.com hardy-updates/main Packages
Ign http://us.archive.ubuntu.com hardy-updates/restricted Packages
Ign http://us.archive.ubuntu.com hardy-updates/main Sources
Ign http://us.archive.ubuntu.com hardy-updates/restricted Sources
Ign http://us.archive.ubuntu.com hardy-updates/universe Packages
Ign http://us.archive.ubuntu.com hardy-updates/universe Sources
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Sources
Err http://us.archive.ubuntu.com hardy/main Packages
  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy/restricted Packages
  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy/main Sources
  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy/restricted Sources
  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy/universe Packages
  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy/universe Sources
  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy/multiverse Packages
  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy/multiverse Sources
  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy-updates/main Packages
  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy-updates/restricted Packages
  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy-updates/main Sources
  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy-updates/restricted Sources
  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy-updates/universe Packages
  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy-updates/universe Sources
  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy-updates/multiverse Packages
  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy-updates/multiverse Sources
  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg  Cannot initiate the connection to security.ubuntu.com:80 (91.189.88.37). - connect (101 Network is unreachable)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2  Cannot initiate the connection to security.ubuntu.com:80 (91.189.88.37). - connect (101 Network is unreachable)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2  Cannot initiate the connection to security.ubuntu.com:80 (91.189.88.37). - connect (101 Network is unreachable)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2  Cannot initiate the connection to security.ubuntu.com:80 (91.189.88.37). - connect (101 Network is unreachable)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2  Cannot initiate the connection to security.ubuntu.com:80 (91.189.88.37). - connect (101 Network is unreachable)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz  Cannot initiate the connection to security.ubuntu.com:80 (91.189.88.37). - connect (101 Network is unreachable)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.gz  Cannot initiate the connection to security.ubuntu.com:80 (91.189.88.37). - connect (101 Network is unreachable)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/source/Sources.gz  Cannot initiate the connection to security.ubuntu.com:80 (91.189.88.37). - connect (101 Network is unreachable)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/source/Sources.gz  Cannot initiate the connection to security.ubuntu.com:80 (91.189.88.37). - connect (101 Network is unreachable)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-i386/Packages.gz  Cannot initiate the connection to security.ubuntu.com:80 (91.189.88.37). - connect (101 Network is unreachable)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/source/Sources.gz  Cannot initiate the connection to security.ubuntu.com:80 (91.189.88.37). - connect (101 Network is unreachable)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.gz  Cannot initiate the connection to security.ubuntu.com:80 (91.189.88.37). - connect (101 Network is unreachable)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/source/Sources.gz  Cannot initiate the connection to security.ubuntu.com:80 (91.189.88.37). - connect (101 Network is unreachable)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.gz  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.gz  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.gz  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.gz  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.gz  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.gz  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.gz  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.gz  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/source/Sources.gz  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.88.40). - connect (101 Network is unreachable) [IP: 91.189.88.40 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.

```Then I tried to ping [http://www.google.com](http://www.google.com)

```
ping: unknown host http://www.google.com
```I can connect to the router, because I'm actually doing all of this remotely from a different computer with putty.


I am using a static IP:

/etc/network/interfaces
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The dhcp  network interface
#auto eth0
#iface eth0 inet dhcp

# The static network interface
 auto eth1
 iface eth1 inet static
 #iface eth1 inet dhcp
        address 192.168.1.100
        netmask 225.225.225.0
        gateway 192.168.1.254

```
/etc/resolv.conf```
search gateway.2wire.net
nameserver 192.168.1.254
```
ipconfig
```
usaconnect@ubuntu:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:02:e3:1c:bb:62
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:e3ff:fe1c:bb62/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:90982395 errors:3 dropped:0 overruns:0 frame:7
          TX packets:112637527 errors:27 dropped:0 overruns:0 carrier:54
          collisions:0 txqueuelen:1000
          RX bytes:2864075090 (2.6 GB)  TX bytes:1023005122 (975.6 MB)
          Interrupt:16 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:869 errors:0 dropped:0 overruns:0 frame:0
          TX packets:869 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:74252 (72.5 KB)  TX bytes:74252 (72.5 KB)

```


Thanks,
Crye

---

### Post by martinbaselier on 2009-07-20
```
ping: unknown host http://www.google.com
```
This suggest a dns problem.

I presume **ping 192.168.1.254** works fine?

Can you **ping 74.125.79.103**? It's one of the ip addresses of google.

If that works, you could either put the dns servers of your provider in /etc/resolv.conf or the opendns ones (208.67.222.222, 208.67.220.220)

---

### Post by crye on 2009-07-21
Just got to work where the server is.

I can ping 192.168.1.254

but I cannot ping Google's IP. 

Any ideas?

---

### Post by martinbaselier on 2009-07-21
In that case it's probably some setting in the router. The connection between the computer and the router works fine. The router should handle the communications between the computer and the outside world.

---

### Post by superprash2003 on 2009-07-21
post output of **sudo iptables -L**

---

### Post by crye on 2009-07-21
```
usaconnect@ubuntu:/backup$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

---

### Post by superprash2003 on 2009-07-22
post output of **route -n**

---

### Post by crye on 2009-07-22
Actually I just fixed it.

I found the following code on the forums and it fixed it

```
sudo route add default gw 192.168.1.254
```

After that it all worked.

Thanks for the help.

---

### Post by realmkeeper on 2009-11-01
> **crye said:**
> Actually I just fixed it.

I found the following code on the forums and it fixed it

```
sudo route add default gw 192.168.1.254
```After that it all worked.

Thanks for the help.


:KS Thank you, thank you, thank you

Started to figure it was something like this. After reading all the other posts describing how to hack the .conf files.

This needs a beer and a cheers from sunny South Africa.

---

