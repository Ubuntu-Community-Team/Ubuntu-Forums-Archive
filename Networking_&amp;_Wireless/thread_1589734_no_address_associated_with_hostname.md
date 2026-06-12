---
title: "no address associated with hostname"
date: 2010-10-06
forum: Networking &amp; Wireless
---

### Post by tottenham12712 on 2010-10-06
ok so when i sudo apt-get update i get a bunch of crap that says no address associated with hostname

ive googled this and changed my /etc/hosts to all sorts of things and no luck:( apache wont even work now either. this server is for a few websites the company i work for hosts. currently i swaped it over to another windows based comp but we want it on ubuntu. 

ive heard this is dns related? and that a FQDN is needed? if so im not sure how to re write my /hosts file but as of not it looks like this:

```
127.0.0.1	localhost
63.119.120.135	speed


# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

im at a loss so any help would be of much help thanks!

---

### Post by Iowan on 2010-10-06
Most of my machines have a line in */etc/hosts* similar to:
 **127.0.1.1 myhostname**. It's usually better to edit */etc/hostname* and */etc/hosts* at the same time - otherwise **sudo** complains.

---

### Post by tottenham12712 on 2010-10-06
ive tried that i get the same error:/

etc/hosts
```
127.0.0.1	localhost
127.0.0.1	speed


# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

etc/hostname

```
speed
```

---

### Post by r939ick on 2010-10-06
It might help if you pasted in the "bunch of crap" you're getting.

How much of your networking setup is working?  Can you ping google.com?  If not, can you ping 8.8.8.8 ?

---

### Post by tottenham12712 on 2010-10-06
only the beginning 

```
speedtest@speed:~$ sudo apt-get update
[sudo] password for speedtest:
0% [Connecting to download.webmin.com] [Connecting to us.archive.ubuntu.com] [Connecting to security.ubuntu.com] [Connecting to archive.canonical.com]127.0.0.1 localhost
127.0.0.1       speed


# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
Err http://security.ubuntu.com lucid-security Release.gpg
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.canonical.com lucid Release.gpg
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Err http://download.webmin.com sarge Release.gpg
  Something wicked happened resolving 'download.webmin.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com lucid Release.gpg
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
0% [Connecting to download.webmin.com] [Connecting to us.archive.ubuntu.com] [Connecting to security.ubuntu.com] [Connecting to archive.canonical.com]
```

apache gets this:

```
Failed to start apache :
 * Starting web server apache2
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
[Wed Oct 06 21:59:37 2010] [warn] NameVirtualHost 63.119.120.140:0 has no VirtualHosts
[Wed Oct 06 21:59:37 2010] [warn] NameVirtualHost *:0 has no VirtualHosts
(2)No such file or directory: apache2: could not open error log file /var/log/apache2/error.log.
Unable to open logs
   ...fail!
```

and i can ping:

```
speedtest@speed:~$ ping www.google.com
PING www.l.google.com (72.14.204.103) 56(84) bytes of data.
64 bytes from iad04s01-in-f103.1e100.net (72.14.204.103): icmp_seq=1 ttl=55 time=61.0 ms
64 bytes from iad04s01-in-f103.1e100.net (72.14.204.103): icmp_seq=2 ttl=55 time=18.6 ms
64 bytes from iad04s01-in-f103.1e100.net (72.14.204.103): icmp_seq=3 ttl=55 time=17.1 ms
64 bytes from iad04s01-in-f103.1e100.net (72.14.204.103): icmp_seq=4 ttl=55 time=16.4 ms
64 bytes from iad04s01-in-f103.1e100.net (72.14.204.103): icmp_seq=5 ttl=55 time=21.4 ms
64 bytes from iad04s01-in-f103.1e100.net (72.14.204.103): icmp_seq=6 ttl=55 time=16.9 ms
64 bytes from iad04s01-in-f103.1e100.net (72.14.204.103): icmp_seq=7 ttl=55 time=18.4 ms
64 bytes from iad04s01-in-f103.1e100.net (72.14.204.103): icmp_seq=8 ttl=55 time=59.9 ms
^C
--- www.l.google.com ping statistics ---
8 packets transmitted, 8 received, 0% packet loss, time 7002ms
rtt min/avg/max/mdev = 16.410/28.747/61.036/18.372 ms
speedtest@speed:~$

```

---

### Post by chili555 on 2010-10-06
Please try:```
127.0.0.1    localhost
127.0.[COLOR="Red"]1[/COLOR].1    speed


# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```Then run update again and let us see the result.

---

### Post by tottenham12712 on 2010-10-06
same thing:/
```
speedtest@speed:~$ sudo apt-get update
[sudo] password for speedtest:
Err http://us.archive.ubuntu.com lucid Release.gpg                             o
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com lucid-security Release.gpg
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://download.webmin.com sarge Release.gpg
  Something wicked happened resolving 'download.webmin.com:http' (-5 - No address associated with hostname)
Err http://archive.canonical.com lucid Release.gpg
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
0% [Connecting to download.webmin.com] [Connecting to us.archive.ubuntu.com]
```

---

### Post by chili555 on 2010-10-06
I am starting to think it's maybe not related to localhost et al. Can you otherwise use the internet? Ping Google?```
ping -c3 www.google.com
```

---

### Post by tottenham12712 on 2010-10-06
yes it pings fine and it surfs the web fine(when i was at our noc, im doing this all remotely now)

```
speedtest@speed:~$ ping www.google.com
PING www.l.google.com (72.14.204.103) 56(84) bytes of data.
64 bytes from iad04s01-in-f103.1e100.net (72.14.204.103): icmp_seq=1 ttl=55 time=61.0 ms
64 bytes from iad04s01-in-f103.1e100.net (72.14.204.103): icmp_seq=2 ttl=55 time=18.6 ms
64 bytes from iad04s01-in-f103.1e100.net (72.14.204.103): icmp_seq=3 ttl=55 time=17.1 ms
64 bytes from iad04s01-in-f103.1e100.net (72.14.204.103): icmp_seq=4 ttl=55 time=16.4 ms
64 bytes from iad04s01-in-f103.1e100.net (72.14.204.103): icmp_seq=5 ttl=55 time=21.4 ms
64 bytes from iad04s01-in-f103.1e100.net (72.14.204.103): icmp_seq=6 ttl=55 time=16.9 ms
64 bytes from iad04s01-in-f103.1e100.net (72.14.204.103): icmp_seq=7 ttl=55 time=18.4 ms
64 bytes from iad04s01-in-f103.1e100.net (72.14.204.103): icmp_seq=8 ttl=55 time=59.9 ms
^C
--- www.l.google.com ping statistics ---
8 packets transmitted, 8 received, 0% packet loss, time 7002ms
rtt min/avg/max/mdev = 16.410/28.747/61.036/18.372 ms
speedtest@speed:~$
```

---

### Post by chili555 on 2010-10-07
I wonder if there is a problem with your /etc/apt/sources.list file. Please post the lines relevant to this:> Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                             o
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://download.webmin.com](http://download.webmin.com) sarge Release.gpg
  Something wicked happened resolving 'download.webmin.com:http' (-5 - No address associated with hostname)
Err [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
I'll compare it to my working file and let's see if there is something amiss.

---

### Post by tottenham12712 on 2010-10-07
this is the whole thing bc all of them say the same thing...

```
# 
# deb cdrom:[Ubuntu-Server 10.04 LTS _Lucid Lynx_ - Release i386 (20100427)]/ lucid main restricted

#deb cdrom:[Ubuntu-Server 10.04 LTS _Lucid Lynx_ - Release i386 (20100427)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://download.webmin.com/download/repository sarge contrib
deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse

```

---

### Post by chili555 on 2010-10-07
> bc all of them say the same thing...They do until we start amending them. For example, mine has, among other changes:> deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) lucid mainI have no way to know if you have made additions and that they are correct until you show me. 

Frankly, I am stumped. Your host and hostname files look correct; your sources.list looks correct and you can ping and surf, which suggests that resolv.conf is also correct. 

I don't know anything else to fix. Maybe one of my colleagues will chime in.

---

### Post by r939ick on 2010-10-07
> **chili555 said:**
> Frankly, I am stumped.

Me, too.  This is an interesting one.  Time to grasp at straws.

Can you `cat /etc/resolv.conf` and `cat /etc/apt/apt.conf` for us please?  Also, maybe try `env | grep proxy` ?

---

### Post by redmk2 on 2010-10-07
What do you get when you try this
[COLOR="Green"]**Edit: **Added a line to become root[/COLOR]```
sudo -i
strace apt-get update
```

---

### Post by tottenham12712 on 2010-10-10
hey guys i wanna thank you for your help so far! so far shes still not working:( i went on vacation this week and i will get you the results to the latest posts on monday, sorry for the delay

---

### Post by tottenham12712 on 2010-10-20
Thanks for all your help guys....turns out the server has a virus:/

[http://ubuntuforums.org/showthread.php?p=10003947#post10003947](http://ubuntuforums.org/showthread.php?p=10003947#post10003947)

i posted a new thread there any input would be much appreciated!

---

### Post by whitemagicwoman on 2010-11-01
I am having this problem too (and I am virus-free).  I would appreciate any suggestions.  

Somehow this seems to be also affecting the wireless capability of that machine or I would include the results of the strace (many pages long).  A lot of "something wicked happened" type messages are what I saw.

---

### Post by redmk2 on 2010-11-01
> **whitemagicwoman said:**
> I am having this problem too (and I am virus-free).  I would appreciate any suggestions.  

Somehow this seems to be also affecting the wireless capability of that machine or I would include the results of the strace (many pages long).  A lot of "something wicked happened" type messages are what I saw.

The "something wicked happened" means that the FQDN could not be resolved (DNS).  The is not your fault.  This is a fault of the name resolution at the site you are trying to connect to.  Maybe your repo list is bad.

---

### Post by whitemagicwoman on 2010-12-17
> **redmk2 said:**
> The "something wicked happened" means that the FQDN could not be resolved (DNS).  The is not your fault.  This is a fault of the name resolution at the site you are trying to connect to.  Maybe your repo list is bad.

Right, I would have thought that, except that the repo list is identical (as far as I can tell) to that on my other machine which IS working.

Is there a way to, say, return the repo list to the defaults, or something?

---

### Post by anthonyhess on 2010-12-17
> **whitemagicwoman said:**
> Right, I would have thought that, except that the repo list is identical (as far as I can tell) to that on my other machine which IS working.

Is there a way to, say, return the repo list to the defaults, or something?

Looks like it has nothing to do with the repos; It is a know bug with Network Manager:

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/574886](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/574886)

There is a work around, by hard-coding a DNS server (such as Google's 8.8.8.8); see post 17 here for directions:

[http://ubuntuforums.org/showthread.php?t=1475399&page=2](http://ubuntuforums.org/showthread.php?t=1475399&page=2)

Anthony

---

### Post by whitemagicwoman on 2010-12-23
Strangely, what worked in my case, which I just tried on a whim, was re-running Update Manager with a hard connection to the Internet rather than just wireless.  Now everything seems to be working okay.  If I have any more problems I will try the DNS fix Anthony mentioned above - it sounds like just the ticket.

wmw

---

### Post by Liova99 on 2011-11-18
I had the same problem when i try to install Klavero for ubuntu 10.4, the problem was that i am from Greece and the synaptic manager setings was for Greek network and now i live in russia, so i change that and it works!!! Because my englesh is not so good i post a foto :) 

[IMG]http://dl.dropbox.com/u/34827065/Screenshot.png[/IMG]

---

### Post by gavv on 2012-09-02
How strange, I was getting the same errors before when I was attempting to do an update through the Update Manager. I didn't know what was going on, so I looked at my host files, resolve.conf files, and some others, but nothing looked amiss. I actually didn't change or edit any files, but somehow I retried the update manager after removing a Intel driver CD I had accidentally left in the CD drive, and it suddenly started working. I don't think that would have fixed the problem, but who knows, the updates are complete now..

---

