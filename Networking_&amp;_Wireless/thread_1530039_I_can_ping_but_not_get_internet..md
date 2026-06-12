---
title: "I can ping but not get internet."
date: 2010-07-13
forum: Networking &amp; Wireless
---

### Post by wlraider70 on 2010-07-13
i have been working a lot on this ubuntu box.

I think i have my reslov.conf correct and i think bind9 is working.

I can ping [www.google.com](www.google.com)

I CANNOT ping 74.125.77.103...I have no ideas.

---

### Post by Iowan on 2010-07-13
What's in the routing table (**route -n**)?

---

### Post by wlraider70 on 2010-07-14
luke@media:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.10.10.0      0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         10.10.10.1      0.0.0.0         UG    100    0        0 eth0



im thinking it might be my reverse DNS.

So I renamed
rev.0.168.192.in-addr.arpa

to

rev.10.10.10.in-addr.arpa

(my ip is 10.10.10 i hope its OK since its the same backwards and forwards.)




rev.10.10.10.in-addr.arpa
```

@ IN SOA ns1.zion.com. media.zion.com.  (
                        2006081401;
                        28800; 
                        604800;
                        604800;
                        86400 
)

                     IN    NS     ns1.zion.com.
1                    IN    PTR    zion.com

```


10.10.10.1 is my router
10.10.10.2 is the box in question also my "server"
its name is media.



hope that helps

---

### Post by Iowan on 2010-07-14
Maybe it's just the different locations, that address doesn't ping for me either, but **ping 74.125.95.147** works...

---

### Post by wlraider70 on 2010-07-14
So i did some work on Firefox and now i can get internet browsing (i turned off ipv6 support.)

however i cannot do apt-get or use synaptic.

here's the ping result

........
ping 74.125.77.103
PING 74.125.77.103 (74.125.77.103) 56(84) bytes of data.
^C
--- 74.125.77.103 ping statistics ---
8 packets transmitted, 0 received, 100% packet loss, time 7056ms

luke@media:~$



edit:


I've been playing with the reverse dns settings.
I can do some stuff:

```

luke@media:~$ host 10.10.10.2
Name: media.ZION.COM
Address: 10.10.10.2
Aliases: media

luke@media:~$ host www.google.com
www.google.com      	CNAME	www.l.google.com
www.l.google.com    	A	66.102.7.104
www.l.google.com    	A	66.102.7.99
luke@media:~$ host 66.102.7.104
Name: lax04s01-in-f104.1e100.net
Address: 66.102.7.104

luke@media:~$ ping 66.102.7.104
PING 66.102.7.104 (66.102.7.104) 56(84) bytes of data.
64 bytes from 66.102.7.104: icmp_seq=1 ttl=54 time=128 ms
64 bytes from 66.102.7.104: icmp_seq=2 ttl=54 time=212 ms
64 bytes from 66.102.7.104: icmp_seq=3 ttl=54 time=110 ms
64 bytes from 66.102.7.104: icmp_seq=4 ttl=54 time=174 ms
^C
--- 66.102.7.104 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 110.904/156.836/212.801/39.864 ms
luke@media:~$ 


```

however if i try apt-get i still get 

```


luke@media:~$ sudo apt-get update
Err http://archive.ubuntu.com jaunty Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com jaunty/main Translation-en_US
 **[COLOR="Red"] Could not resolve 'archive.ubuntu.com'[/COLOR]**
Err http://archive.ubuntu.com jaunty/restricted Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com jaunty/universe Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com jaunty/multiverse Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com jaunty-updates Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com jaunty-updates/main Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com jaunty-updates/restricted Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com jaunty-updates/universe Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://security.ubuntu.com jaunty-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com jaunty-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com jaunty-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com jaunty-security/multiverse Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com jaunty-security/universe Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://linux.dropbox.com jaunty Release.gpg
  Could not resolve 'linux.dropbox.com'
Err http://linux.dropbox.com jaunty/main Translation-en_US
  Could not resolve 'linux.dropbox.com'
Reading package lists... Done
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://linux.dropbox.com/ubuntu/dists/jaunty/Release.gpg  Could not resolve 'linux.dropbox.com'

W: Failed to fetch http://linux.dropbox.com/ubuntu/dists/jaunty/main/i18n/Translation-en_US.bz2  Could not resolve 'linux.dropbox.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
luke@media:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


```

---

### Post by wlraider70 on 2010-07-18
Dear future reader.


It appears my error had several parts

1) was getting my bind9 up and running
2) was the IPv6
3) an off shoot of 2 was a bug in 9.04 see here ([https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/313218](https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/313218))


the solution was upgrading to the next distro.
disabling ipv6 in Firefox via "about:config"
fixing up bind files


good luck.

---

