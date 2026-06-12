---
title: "Destination unreachable"
date: 2013-05-09
forum: Networking &amp; Wireless
---

### Post by JKyleOKC on 2013-05-09
I'm continually getting error messages from my local DNS server, such as this small example:```
May  8 10:43:54 mehitabel named[1086]: error (network unreachable) resolving 'sa.bbc.com/A/IN': 2001:503:231d::2:30#53
May  8 10:43:54 mehitabel named[1086]: error (network unreachable) resolving 'sa.bbc.com/A/IN': 2001:503:a83e::2:30#53
May  8 10:43:54 mehitabel named[1086]: error (network unreachable) resolving 'static.bbc.co.uk/A/IN': 2001:502:ad09::3#53
May  8 10:43:54 mehitabel named[1086]: error (network unreachable) resolving 'static.bbc.co.uk/A/IN': 2a01:40:1001:35::2#53
May  8 10:43:55 mehitabel named[1086]: error (network unreachable) resolving 'open.live.bbc.co.uk/A/IN': 2001:502:ad09::3#53
May  8 10:43:55 mehitabel named[1086]: error (network unreachable) resolving 'secure-us.imrworldwide.com/A/IN': 2001:503:231d::2:30#53
May  8 10:43:57 mehitabel named[1086]: success resolving 'secure-us.imrworldwide.com/A' (in 'imrworldwide.com'?) after reducing the advertised EDNS UDP packet size to 512 octets
May  8 10:43:57 mehitabel named[1086]: success resolving 'open.live.bbc.co.uk/A' (in 'bbc.co.uk'?) after reducing the advertised EDNS UDP packet size to 512 octets

```However I've attempted to turn off EDNS in named.conf, and also to limit its packet size to 512 octets.

The strange thing I notice is that all of these messages deal with v6 addresses; they never show a v4 address. All of the threads I've found on Google indicate a firewall problem, but I have no v6 firewall configured... Any ideas to help me troubleshoot this? Could it be a problem at my ISP's servers, which I've configured as forwarders?

EDIT: Attempting to do "nslookup" on the addresses returns "Host unknown" from my ISP's server; AT&T apparently doesn't yet support DNS for v6!

---

### Post by Warprunner on 2013-05-09
If you want to disable IPV6 I found this post for you...
[http://ubuntuforums.org/showthread.php?t=87798&highlight=turn+ipv6](http://ubuntuforums.org/showthread.php?t=87798&highlight=turn+ipv6)

---

### Post by JKyleOKC on 2013-05-09
Do you think that will work on Lucid? I noted that Karmic moved the support from a module into the kernel itself, so I apparently need a kernel parameter to turn it off. And I'll be moving to 12.04 soon since Lucid is about to go EOL...

---

### Post by varunendra on 2013-05-09
> **Warprunner said:**
> If you want to disable IPV6 I found this post for you...
[http://ubuntuforums.org/showthread.php?t=87798&highlight=turn+ipv6](http://ubuntuforums.org/showthread.php?t=87798&highlight=turn+ipv6)

Wow! A post from 2005! Didn't read much after reading the date :)

As for current versions, this is how IPv6 is disabled permanently (of course can be reverted if required so) -
Add these lines to the /etc/sysctl.conf file :
> # disable IPv6
net.ipv6.conf.all.disable_ipv6=1
net.ipv6.conf.default.disable_ipv6=1
net.ipv6.conf.lo.disable_ipv6=1

A single command to do this :
```
echo -e "\n# disable IPv6\nnet.ipv6.conf.all.disable_ipv6=1\nnet.ipv6.conf.default.disable_ipv6=1\nnet.ipv6.conf.lo.disable_ipv6=1" | sudo tee -a /etc/sysctl.conf
```

Additionally, set IPv6 "Method" to "Ignore" in Network Manager.
Hopefully this gets rid of the error messages.


**PS:**
Apparently, Lucid Desktop, along with Hardy Server, reached its EOL today : [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
Although the repositories will stay there for a while before they'll be moved from archive.ubuntu.com to old-releases.ubuntu.com

---

### Post by JKyleOKC on 2013-05-09
Many thanks! I've totally disabled Network Manager on this system, and use the interfaces file instead. I'll be staying with Lucid for a few more weeks, since I have some 300 GB of VMs on it that I'll need to back up for safety before starting to upgrade, and it'll then take me at least a week to get all my servers that run on the system (DNS, FTP, PostFix, and LAN router) back into action after making the change!

---

### Post by varunendra on 2013-05-09
> **JKyleOKC said:**
> ...since I have some 300 GB of VMs..
.... only? :lolflag:

---

