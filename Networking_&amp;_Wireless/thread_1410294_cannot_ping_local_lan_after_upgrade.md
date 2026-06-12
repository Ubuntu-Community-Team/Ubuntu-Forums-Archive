---
title: "cannot ping local lan after upgrade"
date: 2010-02-18
forum: Networking &amp; Wireless
---

### Post by alixixi on 2010-02-18
when I installed 6.10 edgy on a DELL server with netXtreme II adaptor I could not pint the local IPs the message was 

Destination Unreachable. 

I resolved that by disabling the ipv6 in /etc/modprob.d/alias file.

I recently upgraded the edgy to feisty and the problem is back. but disabling the ipv6 does not seem to help this time! 

i get destination unreachable when i ping any machine in the LAN. I can pint the localhost or 127.0.0.1 but no the gateway or anything else. 

any idea anyone? my prior appreciations.

---

### Post by wojox on 2010-02-18
Try:

```
sudo nano /etc/default/grub
```

Change:

```
GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash&#8221;
```

To:

```
GRUB_CMDLINE_LINUX_DEFAULT=&#8221;ipv6.disable=1 quiet splash&#8221;
```

Reboot.

---

