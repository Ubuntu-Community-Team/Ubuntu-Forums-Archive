---
title: "Empty resolv.conf, short names not working"
date: 2012-08-31
forum: Networking &amp; Wireless
---

### Post by luvshines on 2012-08-31
Installed 12.04 recently on Thinkpad T420.

Things were working fine but don't know what might have screwed up the network manager.
Many a times, after connecting to wired LAN on office network, the resolv.conf comes up empty and I am unable to connect to the office servers with shortnames
If I change the resolv.conf manually, then switching from wired lan to my usb dongle at home doesn't change resolv.conf and I again run into issues connecting since it is still looking for DNS pointing to office IPs

Not sure how I reached this state :)
Any ideaz how to fix this ?

---

### Post by luvshines on 2012-09-01
Bumping this !!

---

### Post by chili555 on 2012-09-01
I don't know the exact answer. I'm no expert despite my bean count. You might look at:```
man hosts
```I suspect you may be able to add the short names to /etc/hosts, roughly like this:```
127.0.0.1	localhost
127.0.1.1	mycomputername

199.88.77.5     www.shortname1.com  short1
199.88.77.6     www.shortname2.com  short2

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```Then, I believe, resolv should work normally unless you do:```
ssh -l chili short1
```Or else:```
firefox short1
```...in which case, you will go to the listed IP address.

---

### Post by luvshines on 2012-09-01
> **chili555 said:**
> I suspect you may be able to add the short names to /etc/hosts

That could have helped me if it were only a couple of servers.
But as I said that I am on office network, and there are hundreds of servers to work with. Won't be able to add entries for each of them :(

The issue which I am observing is intermittent.

---

### Post by luvshines on 2012-09-04
Any suggestions ??

Need to fix this. The file is either left blank or the old entries put there by my wifi or USB dongle are not deleted :(

---

### Post by luvshines on 2012-09-10
Ah!!

How can I miss this
[http://askubuntu.com/questions/137037/network-manager-not-populating-resolv-conf](http://askubuntu.com/questions/137037/network-manager-not-populating-resolv-conf)

Nice, that fixed it. easy-peasy :)

---

