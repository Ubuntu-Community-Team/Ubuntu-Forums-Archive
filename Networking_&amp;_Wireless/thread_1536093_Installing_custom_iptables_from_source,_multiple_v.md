---
title: "Installing custom iptables from source, multiple versions?"
date: 2010-07-21
forum: Networking &amp; Wireless
---

### Post by coryj on 2010-07-21
I've been attempting to use a server with 10.04 desktop installed as a packet classifier using l7 filter: [http://l7-filter.sourceforge.net/. ]("http://l7-filter.sourceforge.net/")

I'm trying to get the kernel version to work. I had other issues with the userspace version, which the site suggests is unreliable anyway. Been using the official kernel howto here: [http://l7-filter.sourceforge.net/HOWTO-kernel](http://l7-filter.sourceforge.net/HOWTO-kernel).

I seem to have successfully patched, built, and installed my kernel. 'uname -a' shows the upgraded kernel version. 

Also required is a patched version of iptables. Copied the files as instructed and gave the configure script the path to my patched kernel, like './configure --with-ksource=/home/cory/linux-2.6.32/'. Then I 'make' and 'make install' with no errors. 

However, now I observe that I have two different iptables binaries:
```

root@probe:~# /sbin/iptables -V
iptables v1.4.4
root@probe:~# /usr/local/sbin/iptables -V
iptables v1.4.8

```and when I try to create a rule using my newly compiled iptables (1.4.8 ):
```

root@probe:~# /usr/local/sbin/iptables -A INPUT -m layer7 --l7proto http
iptables: No chain/target/match by that name.

```It seems like iptables is installed in /usr/local/sbin, but the old version running in /sbin is the "active" one that is actually filtering traffic. How can I see which iptables is running, or disable the default version? I'm sure there are scripts I have to modify, etc, in order to replace my iptables.

---

### Post by coryj on 2010-07-22
Bump...

...has anyone gotten the kernel edition of l7-filter working in ubuntu?
Or compiled their own iptables? 

Any hint or reference would be appreciated.

---

