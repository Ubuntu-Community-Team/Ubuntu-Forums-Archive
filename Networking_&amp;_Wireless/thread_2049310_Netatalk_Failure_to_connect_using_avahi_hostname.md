---
title: "Netatalk Failure to connect using avahi hostname"
date: 2012-08-28
forum: Networking &amp; Wireless
---

### Post by lucac81 on 2012-08-28
Hello, I'm scratching my head with this problem.
Using ubuntu 12.04 to try to share my home and other disk to my mac.
Followed various guides with a strange result:
AFP Shares work without problems if I access them with the IP address (on mac CMD+K and go to afp://192.168.1.3) but if I access the host from the finder automatic discovery I get a Connection failed error.
This happens using Mountain Lion 10.8.1
Any thought of this?
After messing with avahi, the hosts file, I find that if I restart avahi and deactivate/reactivate airport sometimes it works...

---

### Post by xdracco on 2012-09-20
we can't help you much unless you post configuration files. I'd start with posting the following files:

/etc/avahi/services/afpd.service
/etc/default/netatalk

I'm able to access via hostname so you've probably just misconfigured something somewhere.

-edit-
Also, make sure you've set up local dns so the hostname can be resolved.. or at the very least, add the entry to /etc/hosts....

---

### Post by jeffrego on 2013-01-19
I just spent a lot of time tracking down an answer to this same problem.  Turns out avahi by default doesn't publish an IPv4 A record on IPv6.  I added the following line to my /etc/avahi/avahi-daemon.conf:
```
publish-a-on-ipv6=yes
```
and restarted avahi-daemon and I could connect to my afp file share from the list in the Finder just fine.

I'm not sure why this was necessary, I installed avahi-utils and looked at the afp shares currently available on the network:
```
avahi-browse -r _afpovertcp._tcp
```
WIthout publish-a-on-ipv6 set to yes, the only record my server was publishing had my IPv6 address.  Once I set that option it started publishing my IPv4 address in the address field.

I also ran this command from my Mac, which told me the Mac couldn't find an IPv6 record for my fileserver either before or after that change:
```
dns-sd -G v4v6 servername
```

---

