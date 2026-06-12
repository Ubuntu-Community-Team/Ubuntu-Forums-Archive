---
title: "Cant access repositories"
date: 2006-06-23
forum: Networking &amp; Wireless
---

### Post by steve_o on 2006-06-23
Regardless of what version of linux I install I am unable to connect to the repositories because they time out.

I can browse the internet perfectly fine, download perfectly fine but in ever distibution I can't access the repositories

I currently have Kubuntu 6.06 installed but it done the same on Suse
10.1 Fedora Core 5.

The message I get when I run apt-get

steve@Steve:~$ sudo apt-get update
Password:
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) dapper Release.gpg
   Could not connect to nz.archive.ubuntu.com:80 (1.0.0.0), connection timed out Failed to fetch  
[http://nz.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://nz.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Co        
                                                        uld not connect to nz.archive.ubuntu.com:80 (1.0.0.0), connection timed out
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource  
temporarily unavail                                                     
           able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is  
another proc                                                            
    ess using it?
steve@Steve:~$

I can only guess it has something to do with the wireless router which is a D-Link G604T, I currently have the firewall on the router and also Kubuntu disabled but still no luck.

The settings in the router are

I have it set as a dhcp server with dns mode set to auto Dns relay selection is set to "user discovered dns server only"
In the Wan section default route and Nat are enabled

---

### Post by oldmanstan on 2006-06-23
well that last error message it is throwing happens when you are trying to run two copies of apt at the same time (for instance, using sudo apt-get when you have synaptic open, the "add remove programs thing also uses apt) so make sure you are only running one "apt" session at a time

as far as why it times out... could you post the contents of your /etc/apt/sources.list file?

---

### Post by steve_o on 2006-06-23
# 
# deb cdrom:[Kubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted 


deb cdrom:[Kubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted 

# Line commented out by installer because it failed to verify:
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) dapper main restricted 
# Line commented out by installer because it failed to verify:
# deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) dapper main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) dapper-updates main restricted 
# Line commented out by installer because it failed to verify:
# deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) dapper-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) dapper universe 
# deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) dapper universe 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse 
# deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse 


# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted 
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted 
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe 
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe 

I have tried enabling them all and disabling them all to see if that works but still no joy

---

### Post by oldmanstan on 2006-06-23
ok, before doing this BACKUP YOUR OLD sources.list file! i don't want to be responsible for messing up your computer...

try this, let us know what happens: uncomment the lines that start with "deb" and "deb-src" except for the section about "backports", read about those in the wiki before you use that section.

now, try changing the "nz" at the beginning of each of the addresses to "us" (i assume you're in new zealand since i think that's what nz is, that way you'll be accessing different servers.

i tried accessing yours (the nz ones) and was able to but they might be blocked for you for some odd reason. this way we can at least tell whether it is your computer or whether the problem is a third party.

for example:
```
deb http://nz.archive.ubuntu.com/ubuntu/ dapper main restricted
```
would become
```
deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
```

lets see if that works

---

### Post by Slim Odds on 2006-06-23
[quote=steve_o]The message I get when I run apt-get

steve@Steve:~$ sudo apt-get update
Password:
Err [http://nz.archive.ubuntu.com]("http://nz.archive.ubuntu.com") dapper Release.gpg
   Could not connect to nz.archive.ubuntu.com:80 (1.0.0.0), connection timed out Failed to fetch  
[http://nz.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg]("http://nz.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg")  Co        
                                                        uld not connect to nz.archive.ubuntu.com:80 (1.0.0.0), connection timed out
E: Could not get lock /var/lib/dpkg/lock - PrivoxyWindowOpen(11 Resource  
temporarily unavail                                                     
           able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is  
another proc                                                            
    ess using it?
steve@Steve:~$
[/quote] 
Slow down everyone. 1.0.0.0 is not the correct address. It looks like you have apt-get set to use a proxy that is not working correctly. Or maybe your DNS settings are weird.

The correct address for nz.archive.ubuntu.com is 202.7.6.9

Until you can properly resolve this address, it's not going to work.

---

### Post by htnprm on 2006-07-01
Hi all. Ubuntu n00b here. Just advising that I've installed 6.06 recently and attempted to run the software updates from the NZ respositories, and I got a lot of download failures due to "Connection reset by peer". I changed to the US repository and the updates all came down in a flash, so I think there may be something wrong with the NZ server.

---

### Post by mips on 2006-07-02
Also have a look at DNS & IPv6

---

### Post by g00n on 2006-07-08
> **Slim Odds said:**
> Slow down everyone. 1.0.0.0 is not the correct address. It looks like you have apt-get set to use a proxy that is not working correctly. Or maybe your DNS settings are weird.

The correct address for nz.archive.ubuntu.com is 202.7.6.9

Until you can properly resolve this address, it's not going to work.

ARGH!!! it's no proxy, it's a problem with the DNS server in the router responding to an IPV6 request with garbage.... REMOVE YOUR ROUTER FROM /etc/resolv.conf and it will work..

This is a workaround, NOT a solution.

---

