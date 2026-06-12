---
title: "Cleaning up /etc/hosts"
date: 2009-12-19
forum: Networking &amp; Wireless
---

### Post by memilanuk on 2009-12-19
Hello all,

Can someone tell me whats up with the 127.0.1.1 entry in /etc/hosts on Ubuntu machines running LAMP stacks?

I don't see it on my Ubunu 9.10 desktop; nor do I see it in any of my other distros - just Ubuntu, and just machines with LAMP installed.  I recall some messages flashing by at boot where Apache (I think) was unable to determine the host name and set the 127.0.1.1 bit.  Like I said, never seen it anywhere else, and since I didn't install a lamp stack to feed a loopback interface, I don't really see the need for it.

Likewise... I have zero intention of doing anything with ipv6 at any time in the near future... so would it make any appreciable difference if I scrubbed all the ipv6 gobblety-gook from my /etc/hosts file?

TIA,

Monte

---

### Post by chili555 on 2009-12-20
> just machines with LAMP installed.Not quite true. The line is present on my machine, associated with the computer's name, viz:```
127.0.0.1	localhost
127.0.1.1	LAPTOP60

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```I am not running LAMP.> so would it make any appreciable difference if I scrubbed I am not sure. I am fairly sure that it will make no appreciable difference if you leave it all there.

If the boot process stumbles on the hostname, I think I'd try to clean that up, rather than remove things that may, or may not be related. What do the logs say?

---

### Post by Iowan on 2009-12-20
There are a few threads where people have tried to change the hostname by editing only */etc/hostname*, and found later that **sudo** complained.

---

### Post by memilanuk on 2009-12-20
> **chili555 said:**
> Not quite true. The line is present on my machine, associated with the computer's name, 


Is your install a server or a desktop?  Maybe thats the difference?  My 9.10 desktop sitting here doesn't have it.

> 
I am not running LAMP.I am not sure. I am fairly sure that it will make no appreciable difference if you leave it all there.


Probably not.  Other than it bothers me ;)  I want to know why Ubuntu has it and other distros don't, and why only some Ubuntu installs at that.

> 
If the boot process stumbles on the hostname, I think I'd try to clean that up, rather than remove things that may, or may not be related. What do the logs say?


Well, as the stuff flew by (on more than one installation, btw) it happens only on boot after initial install; the line gets installed and then I never see the message again.  If it happens during initial boot, then I've had very little opportunity to change or 'fix' things, have I ;)

---

### Post by chili555 on 2009-12-20
> Is your install a server or a desktop? A laptop. If it were a server, I'd most likely be running LAMP, no?> If it happens during initial boot, then I've had very little opportunity to change or 'fix' things, have IQuite right. I thought, from your original post, that the issue was on *every* boot, not just initial boot. Sorry if I misunderstood.

I don't precisely understand how or why Ubuntu does quite a few things. I *do* know that I've never had good luck removing things that I don't precisely understand. I wish I had a more informative answer.

---

### Post by capscrew on 2009-12-20
the file /etc/**hosts **file is a mapping of IP addresses to hostnames (or hostname aliases).  This should not be confused with /etc/**hostname** which sets the hostname of the device (host).

The entire range of 127.0.0.0/8 represents the virtual interface (e.g. lo (loopback)).  This is the **localhost**.  So if you wanted to have a hostname for your loopback interface you could use **ANY** address in the 127.0.0.0/8 range.

Some applications use this feature to to set a unique localhost name for operation.  It is possible that if you remove or alter this mapping that the application will complain or worse yet, fail.

---

### Post by memilanuk on 2009-12-20
> **chili555 said:**
> A laptop. If it were a server, I'd most likely be running LAMP, no? Not necessarily... lots of other 'server' uses besides LAMP, and LAMP can be run from a desktop (or laptop) at that.

But yes, I know what you mean. ;)

capscrew,

Yep, I know that.  My question is: why does Ubuntu feel the need (i.e. what specific requirement are they fullfilling) by creating that extra address mapping?  No other distro that I know of does it quite like that, and I'm kind of wondering 'why'.  AFAIK, the other distros will throw some conglomeration like 

```

127.0.0.1    localhost.localdomain    localhost    foo.local    foo

```

All on one line.  Usually the first thing I do when dressing up the /etc/hosts file on those machines will be to change that to:

```

127.0.0.1    localhost.localdomain    localhost

<ipv6 gobblety-gook>

# local machine
10.0.0.1     foo.local     foo

# rest of LAN
10.0.0.2     bar.local     bar
10.0.0.3     baz.local     baz


```


...because I don't want 'foo.local' to map to a loopback address; I want it on one of the network interfaces.

Now I'm wondering if the 127.0.1.1 business is just a variation on putting all the local host names on one line?

Any ideas on where I'd find someone who knows the answer?

Monte

---

### Post by Iowan on 2009-12-20
> **capscrew said:**
> the file /etc/**hosts **file is a mapping of IP addresses to hostnames (or hostname aliases).  This should not be confused with /etc/**hostname** which sets the hostname of the device (host).
I kinda left a loose end... To manually change a hostname, both */etc/hosts* and */etc/hostname* need to be changed - otherwise **sudo** complains **sudo: unable to resolv host**.

I suspect you are correct on Ubuntu's file being "a variation on putting all the local host names on one line".

---

### Post by capscrew on 2009-12-20
> **memilanuk said:**
> Not necessarily... lots of other 'server' uses besides LAMP, and LAMP can be run from a desktop (or laptop) at that.

But yes, I know what you mean. ;)

capscrew,

Yep, I know that.  My question is: why does Ubuntu feel the need (i.e. what specific requirement are they fullfilling) by creating that extra address mapping?  

No other distro that I know of does it quite like that, and I'm kind of wondering 'why'.  AFAIK, the other distros will throw some conglomeration like 

```

127.0.0.1    localhost.localdomain    localhost    foo.local    foo

```

All on one line.  Usually the first thing I do when dressing up the /etc/hosts file on those machines will be to change that to:

```

127.0.0.1    localhost.localdomain    localhost

<ipv6 gobblety-gook>

# local machine
10.0.0.1     foo.local     foo

# rest of LAN
10.0.0.2     bar.local     bar
10.0.0.3     baz.local     baz


```


...because I don't want 'foo.local' to map to a loopback address; I want it on one of the network interfaces.

Now I'm wondering if the 127.0.1.1 business is just a variation on putting all the local host names on one line?

Any ideas on where I'd find someone who knows the answer?

Monte

I think the use of the loopback is really up to each developer.  The interface is only useful internally on any host.  You could say it is its own domain and therefore not related to any other interface on the localhost or in the LAN.

The only uses AKAIK would be to test the IP stack and to setup configuration for some applications.  Any app that you wanted only local control could use the looopback interface.  Samba SWAT is one example that comes to mind.

As 127.0.0.1 and 127.0.1.1 (and any other address from .0 to .255.255.255 with the prefix of 127) refer to the same virtual interface it really doesn't matter whether the hostname mappings are on one line or separate lines.  Just a guess now; it could be easier to write a script to insert a name/address mapping.

[_[COLOR="DarkSlateGray"]**Here is more information on the loopback interface.**[/COLOR]_]("http://infao5501.ag5.mpi-sb.mpg.de:8080/topx/archive?link=Wikipedia-Lip6-2/569755.xml&style")

Iowan, as to your: 
> I kinda left a loose end... To manually change a hostname, both /etc/hosts and /etc/hostname need to be changed - otherwise sudo complains sudo: unable to resolv host.

If we change the host name (the /etc/hostname file) and not the mapping to the eth0 interface, then the call to the new hostname is unresolvable.  I am supposing that sudo resolves hostnames via the /etc/hosts file.  So the steps are: 1. change hostname and 2. revise the mapping of the IP address to the new hostname.

---

