---
title: "is IPv6 working? Can i use it?"
date: 2010-07-15
forum: Networking &amp; Wireless
---

### Post by wlraider70 on 2010-07-15
I wanted to know more about ipv6. is there a guide?



I'm having some networking and DNS issues. I think it might be related to IPv6 and this bug [https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/313218](https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/313218)

my system is a dd-wrt router -> my server (the box in question)
Its running bind9.


some of the stuff I'm trying to answer. 

How do i set up an address?
How do i verify connection?
How do i set bind9 to resolve
Can my isp handle IPv6?
and so on.

---

### Post by gr4nf on 2010-07-15
IPv6 should work with some extra software installed... can't imagine what you'd be using if for, though i doubt it is causing your DNS issues.

could you post your /etc/network/interfaces file?

To set up static IP, just go to your network connections manager in the "System" drop down menu, delete your current connections, and create one that matches your setup with static IP instead of DHCP. Or you could just edit your interfaces file with:
```

auto eth0
iface eth0 inet static
address "whatever address you want"
netmask 255.255.255.0
network 192.168.0.0 (probably. may differ based on your network)
broadcast 192.168.0.255 (first two numbers should still match with network)
gateway 192.168.0.1 (again, match with network)

```

EDIT:

To verify connection, use the command:
```

ping google.com

```
which will only work if DNS is in order, or just:
```

ping 66.249.92.104

```
which should work even if DNS is broken.

---

### Post by wlraider70 on 2010-07-15
if you go here.

[http://ubuntuforums.org/showthread.php?t=1530039](http://ubuntuforums.org/showthread.php?t=1530039)

you can see some the back story.



I can ping google.com
I can ping an ip.

I could not browse Firefox till i turned off IPv6. (in about:config)
I "Could not resolve 'archive.ubuntu.com'" until i add them manually to the hosts file, then i could update.


I'll post the files when i get home.
I do have a static IP set up for this box.



I am open to ANY suggestions.

---

