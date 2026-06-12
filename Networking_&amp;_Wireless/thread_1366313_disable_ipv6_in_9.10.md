---
title: "disable ipv6 in 9.10"
date: 2009-12-28
forum: Networking &amp; Wireless
---

### Post by ledererster on 2009-12-28
How do you disable ipv6 in 9.10 permanently?  I found a site that has me edit the grub file but it doesn't exist.  One way I found was using this command in the root terminal ```
echo 1 > /proc/sys/net/ipv6/conf/all/disable_ipv6
```

but it's only temporary. I have to do it everytime I reboot.  Is there a way I can do it permanently in 9.10?  Thanks.

---

### Post by bryonak on 2009-12-28
You can have it executed at system boot... press Alt+F2 and type ```
gksudo gedit /etc/rc.local
```
In the editor, add your command right above the "exit 0".




For the record, for some time I used the following script (saved as /usr/bin/disable-ipv6.sh) for this purpose:
```

#!/bin/sh
# disable-ipv6.sh - Disables IPv6 on a specified
# device or eth0 if no argument is given.

if [ "$1" ]; then IFACE=$1;
else IFACE='eth0';
fi

IPV6=`ifconfig $IFACE | gawk '/inet6/ print $3'`;
sudo ifconfig $IFACE inet6 del $IPV6;

```
together with a "/usr/bin/disable-ipv6.sh" entry in my rc.local.
But your approach seems even simpler ;)

---

### Post by ledererster on 2009-12-28
Thanks a lot! I just need to get a new router that likes IPV6 so I don't have to mess with this stuff. Thanks again.

---

### Post by xsr on 2010-03-09
Finally an approach that actually works on Lucid (10.04) server[B]. Thanks!
[/B]

---

