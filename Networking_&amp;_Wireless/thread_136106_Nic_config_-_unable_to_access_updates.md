---
title: "Nic config - unable to access updates"
date: 2006-02-25
forum: Networking &amp; Wireless
---

### Post by caffine_fizz on 2006-02-25
hi,

i'm about 48 hours new to linux so be gentle with me. i recently installed breezy badger to an old system i have; to set it up as a server. Its running two nics one that i want to access the web and another that i want only for my home network to access.

The main problem is i cant seem to run:

atp-get update

it gives off errors that give me the impression its not connecting to the net (i can ping the router through).

linux nic1 ip: 192.168.70.201 (web access)
linux nic2 ip: 192.168.70.201 (home access)
web router ip: 192.168.70.1
home router ip: 192.168.70.2

/etc/network/interfaces is configured as follows:

--------------------------------------------------------------------------
auto lo
iface lo inet loopback

mapping hotplug
            script grep
            map eth0

auto eth0
iface eth0 inet static
             address 192.168.70.201
             netmask 255.255.255.0
             network 192.168.70.0
             broadcast 192.168.70.255
             gateway 192.168.70.1
auto eth1
iface eth1 inet static
             address 192.168.70.202
             netmask 255.255.255.0
             network 192.168.70.0
             broadcast 192.168.70.255
             gateway 192.168.70.2

--------------------------------------------------------------------------

/etc/resolv.conf is set as follows:

--------------------------------------------------------------------------

nameserver 220.233.0.4 220.233.0.3

--------------------------------------------------------------------------

which are the primary and secondary DNS of my isp

/etc/hosts is set as follows

--------------------------------------------------------------------------

127.0.0.1 localhost.localdomain         localhost             server1
192.168.70.201 server1.example.com     server1
192.168.70.202 virtual-ipl.example.com       server1

#The following lines are desirable for IPv6 capable hosts
::1        ip6-localhost    ipv6-loopback
fe00::0  ip6-localnet
fe00::0  ip6-mcastprefix
fe02::1  ip6-allnodes
fe02::2  ip6-allrouters
fe02::3  ip6-allhosts

--------------------------------------------------------------------------

i think this is where the problem is but being a linux noob i've no idea?

---

### Post by claes on 2006-02-25
> /etc/resolv.conf is set as follows:

--------------------------------------------------------------------------

nameserver 220.233.0.4 220.233.0.3

--------------------------------------------------------------------------

which are the primary and secondary DNS of my isp


Change this so it looks like this:

nameserver 220.233.0.4
nameserver 220.233.0.3

And try again. No reboot is needed ofcourse..

Claes

---

### Post by caffine_fizz on 2006-02-25
nagh tried this, then run:

apt-get update

it looks like it going to work getting to 
50%[Connecting to au.archive.ubuntu.com] [Connecting to security.ubuntu.com]
then it hangs for a minute before saying 
Temporary failure resolving 'au.archive.ubuntu.com'
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy Release.gpg
Temporary failure resolving 'security.ubuntu.com'
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-security Release.gpg
It then tries to make another connection again hanging at 50% before spitting out a whole heap of garble that wont allow time for me to document it, something about:
w:Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-security/restricted Packages...........................................

i forgot to mention previosly that i also edited my sources.list as instructed by the guide i'm following at: [http://www.howtoforge.com/perfect_setup_ubuntu_5.10_p3](http://www.howtoforge.com/perfect_setup_ubuntu_5.10_p3)

as follows:

--------------------------------------------------------------------------
# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricteddeb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
--------------------------------------------------------------------------

does this help? sorry i forgot to mention it.

---

### Post by caffine_fizz on 2006-02-25
SOMEONE please help this is driving me nuts!!!!\\:D/

---

### Post by claes on 2006-02-25
To me it looks like it's name resolution that don't work.

If you try: 
host -vv au.archive.ubuntu.com

What does that answer?

Claes

---

### Post by ranf on 2006-02-25
[QUOTE=caffine_fizz]
linux nic1 ip: 192.168.70.201 (web access)
linux nic2 ip: 192.168.70.201 (home access)
web router ip: 192.168.70.1
home router ip: 192.168.70.2
[/QUOTE]
You physically have two different nets. 
Try putting nic2 on a different IP subnet (192.168.71.* for instance).

---

### Post by caffine_fizz on 2006-02-25
[QUOTE=claes]To me it looks like it's name resolution that don't work.

If you try: 
host -vv au.archive.ubuntu.com

What does that answer?

Claes[/QUOTE]

I tried this getting the following responce:
Trying "au.archive.ubuntu.com"
;; connection timed out; no servers could be reached

I also have the DNS set to the way you suguested in you previos post.

---

### Post by caffine_fizz on 2006-02-25
[QUOTE=ranf]You physically have two different nets. 
Try putting nic2 on a different IP subnet (192.168.71.* for instance).[/QUOTE]

this makes sence so i reconfigured it, but still no luck!

---

### Post by caffine_fizz on 2006-02-25
can someone please help that knows something of network configuration and where it is that i'm going astray

---

### Post by Lambert on 2006-02-26
You do need to set up different sub nets as ranf stated.

So nic 1 and that router should be 192.168.70.x

nic 2 and router should be at 192.168.71.x

Your routing table should have the 192.168.70.1 router as the default gateway
and anything in the subnet of 192.168.71.x should be router 2

So I'm not sure exactly how to do this as I haven't but I can suggest trying this.


Under eth0 in your interfaces file add a line like this.

```
gateway 192.168.70.1
``` 
this makes this interface and the internet router your default gateway.

under eth1 you can add a line like this but I can't say if this is proper.

```
post-up route add -net 192.168.71.1 netmask 255.255.255.0 dev eth1
``` 
this should add  routes so all traffic destined for 192.168.71.x will go through eth1 and stay on your home network, everything else will flow towards eth0, the default gateway.

Just make sure you input all the correct ip numbers. My above goes like this.

eth0 = internet interface going to router with ip address 192.168.70.1
eth1 = home network going to router with ip address of 192.168.71.1

---

### Post by caffine_fizz on 2006-02-26
That did it :D 

Thanx man, updated no problems at all. 

cheers \\:D/

---

