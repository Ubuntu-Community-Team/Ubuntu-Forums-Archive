---
title: "networking restart not starting"
date: 2006-03-07
forum: Networking &amp; Wireless
---

### Post by k1ll1nt1m3 on 2006-03-07
I have installed kubuntu on a friends pc and it worked fine for a few months.  Now I cant get the network to start at boot.  If I do [PHP]sudo /etc/init.d/networking restart[/PHP] I get this error.[PHP]/etc/init.d/networking restart
/etc/init.d/networking: line 20: /proc/sys/net/ipv4/conf/all/rp_filter: Permission denied
/etc/init.d/networking: line 20: /proc/sys/net/ipv4/conf/default/rp_filter: Permission denied
/etc/init.d/networking: line 20: /proc/sys/net/ipv4/conf/eth0/rp_filter: Permission denied
 * Reconfiguring network interfaces...                                   [fail][/PHP]

I even did a [PHP]chmod 0777 */rp_filter[/PHP] but I still cant get the network to start right.  I was able to hack around and get a temp fix though.

I was wondering how I could reinstall the packages for the network stuff.  Also, what all would I need to reinstall?  Or any other ideas?

I dont know too much about ubuntu.  I use Gentoo (sorry!!!).  Thanks for any help

---

### Post by k1ll1nt1m3 on 2006-03-15
Thanks.  Ill just switch it to Gentoo.

---

