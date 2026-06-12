---
title: "Intrepid dhclient hook scripts not running"
date: 2009-01-11
forum: Networking &amp; Wireless
---

### Post by at465 on 2009-01-11
Hi

I wrote a dhclient hook script when I was using Hardy, which allows me to automatically update my bind forwarders to the dhcp nameservers, whilst updating my resolv.conf to use localhost as the nameserver. This allows me to run my own personal bind server on my laptop, whilst automatically working with any network's nameservers.

The problem is Intrepid seems to no longer use dhclient-script to run these scripts.

I updated /etc/dhcp3/dhclient.conf to have the script:

script "/sbin/dhclient-script";

but with those changes I can no longer connect to the network.


Is there a new place I can put my hook script to do this? Its important that it updates the bind configuration and restarts bind, so I can't just get away with forcing the nameserver to be localhost in that conf.



For reference, here's the script:

/etc/dhcp3/dhclient-exit-hooks.d/zzzzz_bind-forwarders:

#!/bin/bash
BIND_IP=127.0.0.1

NAMED_FORWARDERS=/etc/bind/named.conf.forwarders
NAMED_INITD=/etc/init.d/bind9
RESOLV_CONF=/etc/resolv.conf

echo $new_domain_name_servers | sed -e '
iforwarders {\n
s/\([^ ]\+\)\s*/    \1;\n/g
a};' > "$NAMED_FORWARDERS"

"$NAMED_INITD" restart

sed -e "
\$anameserver $BIND_IP
/^\s*nameserver/i# moved following nameserver to bind forwarders
s/^\s*nameserver/# nameserver/" -i "$RESOLV_CONF"

---

### Post by at465 on 2009-01-11
I guess I should also note, running /sbin/dhclient-script manually works.

I did an upgrade to get Hardy to Intrepid

---

### Post by perlhead on 2009-02-17
Same problem here... dhclient3 doesn't even seem to run /sbin/dhclient-script, let alone the hooks. I still can't figure out why (or how to fix it).

---

### Post by perlhead on 2009-02-17
OK, found it. The problem is not with dhclient3 itself, but with NetworkManager, which invokes dhclient3 with it's own script file. This script file, however, turns out not to be a script at all, but a compiled program, which runs all files in [FONT=Fixedsys]/etc/NetworkManager/dispatcher.d[/FONT], as pointed out in [this bug report]("https://bugzilla.redhat.com/show_bug.cgi?id=446631").

So I guess it's not a bug, but a feature (albeit undocumented).

---

### Post by at465 on 2009-03-08
I have made a solution to this problem, so that dhclient calls the hooks as well as NetworkManager's script.

[http://www.webtatic.com/blog/2009/03/workaround-so-networkmanager-runs-dhclient-hooks/](http://www.webtatic.com/blog/2009/03/workaround-so-networkmanager-runs-dhclient-hooks/)

Thanks for your help. I wouldn't have been able to figure this out without it.

---

