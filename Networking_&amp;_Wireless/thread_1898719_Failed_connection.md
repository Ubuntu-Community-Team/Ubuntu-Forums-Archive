---
title: "Failed connection"
date: 2011-12-22
forum: Networking &amp; Wireless
---

### Post by temporizer on 2011-12-22
I have ubuntu 11.04 installed.

I am able to go to any website, play any web games, but when it comes to downloading updates, installing packages via software center or installing packages via apt-get, it fails every time.

Is there someone that can help me figure out what is wrong?

thanks

---

### Post by temporizer on 2011-12-22
*bump*

---

### Post by jonobr on 2011-12-22
So what happens when you go to a terminal <application-> accessories> and install something
```
sudo apt-get install someprogram 
```

what happens?

What happens when you do

```
sudo apt-get update
sudo apt-get upgrade
```
any joy there?

---

### Post by temporizer on 2011-12-23
I don't understand. when i do those it comes up with this.

```
20:55:27 | home@home:~$ sudo apt-get install alarm-clock
[sudo] password for home: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package alarm-clock

20:56:24 | home@home:~$ sudo apt-get update
Err http://archive.canonical.com natty InRelease                                                                       
  
Err http://archive.canonical.com natty Release.gpg                                                                     
  Unable to connect to archive.canonical.com:http:
Err http://extras.ubuntu.com natty InRelease                                                          
  
Err http://extras.ubuntu.com natty Release.gpg                                                        
  Unable to connect to extras.ubuntu.com:http:
Err http://archive.ubuntu.com natty InRelease        
  
Err http://archive.ubuntu.com natty-updates InRelease
  
Err http://archive.ubuntu.com natty-security InRelease
  
Err http://archive.ubuntu.com natty Release.gpg      
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.180 1030]
Err http://archive.ubuntu.com natty-updates Release.gpg
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.180 1030]
Err http://archive.ubuntu.com natty-security Release.gpg
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.180 1030]
Reading package lists... Done
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty/InRelease  

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-updates/InRelease  

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-security/InRelease  

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/natty/InRelease  

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/natty/InRelease  

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/natty/Release.gpg  Unable to connect to archive.canonical.com:http:

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty/Release.gpg  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.180 1030]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-updates/Release.gpg  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.180 1030]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-security/Release.gpg  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.180 1030]

W: Some index files failed to download. They have been ignored, or old ones used instead.

20:57:04 | home@home:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
20:57:10 | home@home:~$ 

```

But, whenever i do a ping. it works. or when i go to any website, it works.

```
20:57:23 | home@home:~$ ping www.google.com
PING www.l.google.com (74.125.127.104) 56(84) bytes of data.
64 bytes from pz-in-f104.1e100.net (74.125.127.104): icmp_req=1 ttl=50 time=34.3 ms
64 bytes from pz-in-f104.1e100.net (74.125.127.104): icmp_req=2 ttl=50 time=34.3 ms
64 bytes from pz-in-f104.1e100.net (74.125.127.104): icmp_req=3 ttl=50 time=37.6 ms
64 bytes from pz-in-f104.1e100.net (74.125.127.104): icmp_req=4 ttl=50 time=34.4 ms
64 bytes from pz-in-f104.1e100.net (74.125.127.104): icmp_req=5 ttl=50 time=34.3 ms
^C
--- www.l.google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4005ms
rtt min/avg/max/mdev = 34.314/35.023/37.615/1.302 ms

21:13:42 | home@home:~$ ping www.wikipedia.org
PING wikipedia-lb.pmtpa.wikimedia.org (208.80.152.201) 56(84) bytes of data.
64 bytes from wikipedia-lb.pmtpa.wikimedia.org (208.80.152.201): icmp_req=1 ttl=51 time=128 ms
64 bytes from wikipedia-lb.pmtpa.wikimedia.org (208.80.152.201): icmp_req=2 ttl=51 time=123 ms
64 bytes from wikipedia-lb.pmtpa.wikimedia.org (208.80.152.201): icmp_req=3 ttl=51 time=122 ms
^C
--- wikipedia-lb.pmtpa.wikimedia.org ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 122.480/124.771/128.163/2.480 ms

21:14:03 | home@home:~$ ping wwww.ubuntuforums.com
PING wwww.ubuntuforums.com (91.189.94.12) 56(84) bytes of data.
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=1 ttl=46 time=159 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=2 ttl=46 time=159 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=3 ttl=46 time=160 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=4 ttl=46 time=158 ms
^C
--- wwww.ubuntuforums.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3001ms
rtt min/avg/max/mdev = 158.666/159.769/160.908/0.794 ms

21:14:18 | home@home:~$ ping www.pandora.com
PING www.pandora.com (208.85.40.50) 56(84) bytes of data.
64 bytes from www.pandora.com (208.85.40.50): icmp_req=1 ttl=247 time=30.5 ms
64 bytes from www.pandora.com (208.85.40.50): icmp_req=2 ttl=247 time=26.4 ms
64 bytes from www.pandora.com (208.85.40.50): icmp_req=3 ttl=247 time=29.9 ms
64 bytes from www.pandora.com (208.85.40.50): icmp_req=4 ttl=247 time=34.0 ms
^C
--- www.pandora.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3005ms
rtt min/avg/max/mdev = 26.478/30.268/34.072/2.703 ms
21:14:48 | home@home:~$ 

```

:( :( No Joy :( :(

---

### Post by wildmanne39 on 2011-12-23
Hi, first change servers and see if you can update.
Thanks

---

### Post by temporizer on 2011-12-23
Still doesn't work.
I tried 10 different servers.
I even click "select best server"

Still Nothing :(

---

### Post by wildmanne39 on 2011-12-23
Hi, open synaptic package manager then click on settings, repositories, other software and uncheck the two ppa's that are giving you the errors.
Thanks

---

### Post by temporizer on 2011-12-23
I unchecked all the ppa's in the Other Software tab, unfortunately, that doesn't help either.

I then unchecked all the other ppa's in the "Ubuntu Software" tab, one by one, but I still get errors until I remove all the ppa's, then I get no errors, but then I am unable to install anything.

Thanks.

---

### Post by wildmanne39 on 2011-12-23
Hi, please post the results of:
```
cat /etc/apt/sources.list

ls /etc/apt/sources.list.d/
```
I am not going to be on much until Monday I have family in town for the holidays.
Thanks

---

### Post by temporizer on 2011-12-23
```
16:37:21 | home@home:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu natty main
# deb-src http://extras.ubuntu.com/ubuntu natty main

16:37:25 | home@home:~$ ls /etc/apt/sources.list.d/
16:37:30 | home@home:~$

```

That is obviously when everything is unchecked. 
Shall I recheck them and post that?

---

### Post by wildmanne39 on 2011-12-23
Hi, yes please recheck all that were checked, then post the results, also make sure you are not behind a proxy server.
Thanks

---

### Post by temporizer on 2011-12-24
```
20:01:46 | home@home:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb http://archive.ubuntu.com/ubuntu natty main universe restricted multiverse
deb-src http://extras.ubuntu.com/ubuntu natty main
20:01:50 | home@home:~$ ls /etc/apt/sources.list.d/
20:01:54 | home@home:~$ 

```

I am not behind a proxy server. also i have 3 other computers on this network that are able to do everything just fine. it's just this one computer. are there any other diagnostics commands i can try to see if this computer isn't connecting correctly?

for starters, this is ifconfig:

```


20:01:54 | home@home:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:ca:44:26:7b  
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:caff:fe44:267b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:360696 errors:11 dropped:204 overruns:11 frame:0
          TX packets:201364 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:60303178 (60.3 MB)  TX bytes:83795488 (83.7 MB)
          Interrupt:18 Base address:0xd400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:135549 errors:0 dropped:0 overruns:0 frame:0
          TX packets:135549 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13050886 (13.0 MB)  TX bytes:13050886 (13.0 MB)

```

---

### Post by wildmanne39 on 2011-12-24
Hi, this is not a network issue if you can connect to the internet it is a package manager issue.

I am going to give you a link to reset your repositories back to default when you first installed ubuntu to see if that fixes the problem.
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)
Thanks

---

### Post by temporizer on 2011-12-24
So, I did what you suggested and replaced the old sources.list with the new sources.list that was generated by that site you linked me to.
Same results.
So I did a little test.
see the following:

```
**23:15:05 | home@home:~$ ping www.google.com**
PING www.l.google.com (74.125.127.147) 56(84) bytes of data.
64 bytes from pz-in-f147.1e100.net (74.125.127.147): icmp_req=1 ttl=50 time=34.9 ms
64 bytes from pz-in-f147.1e100.net (74.125.127.147): icmp_req=2 ttl=50 time=36.4 ms
64 bytes from pz-in-f147.1e100.net (74.125.127.147): icmp_req=3 ttl=50 time=33.7 ms
c64 bytes from pz-in-f147.1e100.net (74.125.127.147): icmp_req=4 ttl=50 time=33.7 ms
64 bytes from pz-in-f147.1e100.net (74.125.127.147): icmp_req=5 ttl=50 time=37.5 ms
64 bytes from pz-in-f147.1e100.net (74.125.127.147): icmp_req=6 ttl=50 time=35.5 ms
^C
--- www.l.google.com ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5005ms
rtt min/avg/max/mdev = 33.701/35.342/37.592/1.417 ms
23:15:13 | home@home:~$ 
23:15:16 | home@home:~$ 
**23:15:16 | home@home:~$ ping http://www.google.com**
ping: unknown host http://www.google.com
23:15:20 | home@home:~$ 
23:15:26 | home@home:~$ 
**23:15:26 | home@home:~$ ping www.ubuntuforums.com**
PING www.ubuntuforums.com (91.189.94.12) 56(84) bytes of data.
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=1 ttl=46 time=159 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=2 ttl=46 time=159 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=3 ttl=46 time=160 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=4 ttl=46 time=159 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=5 ttl=46 time=158 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=6 ttl=46 time=161 ms
^C
--- www.ubuntuforums.com ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5004ms
rtt min/avg/max/mdev = 158.625/159.919/161.321/0.809 ms
**23:15:37 | home@home:~$ ping http://www.ubuntuforums.com**
ping: unknown host http://www.ubuntuforums.com
23:15:44 | home@home:~$ 
23:16:41 | home@home:~$ 
**23:16:42 | home@home:~$ ping www.wikipedia.org**
PING wikipedia-lb.pmtpa.wikimedia.org (208.80.152.201) 56(84) bytes of data.
64 bytes from wikipedia-lb.pmtpa.wikimedia.org (208.80.152.201): icmp_req=1 ttl=51 time=123 ms
64 bytes from wikipedia-lb.pmtpa.wikimedia.org (208.80.152.201): icmp_req=2 ttl=51 time=128 ms
64 bytes from wikipedia-lb.pmtpa.wikimedia.org (208.80.152.201): icmp_req=3 ttl=51 time=126 ms
64 bytes from wikipedia-lb.pmtpa.wikimedia.org (208.80.152.201): icmp_req=4 ttl=51 time=128 ms
64 bytes from wikipedia-lb.pmtpa.wikimedia.org (208.80.152.201): icmp_req=5 ttl=51 time=134 ms
^C
--- wikipedia-lb.pmtpa.wikimedia.org ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4001ms
rtt min/avg/max/mdev = 123.837/128.334/134.390/3.470 ms
**23:16:52 | home@home:~$ ping http://www.wikipedia.org**
ping: unknown host http://www.wikipedia.org
23:16:58 | home@home:~$ 

```

Notice that when I ping a site without the http:// it works fine, but when I add the http:// it fails.

Whats that all about?

it looks like it has something to do with my hosts file... unsure tho.

also when I ping ping us.archive.ubuntu.com/ubuntu it also fails.

---

### Post by wildmanne39 on 2011-12-24
Hi, I am out of idea's on this one.
Thanks

---

### Post by temporizer on 2011-12-24
Thanks for your help.

Anyone else have any ideas?

---

### Post by temporizer on 2012-01-01
I still haven't fixed the issue. anyone have any ideas?

---

