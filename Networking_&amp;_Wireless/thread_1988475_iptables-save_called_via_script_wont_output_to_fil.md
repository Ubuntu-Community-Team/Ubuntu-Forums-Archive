---
title: "iptables-save called via script wont output to file"
date: 2012-05-27
forum: Networking &amp; Wireless
---

### Post by TroLLATM on 2012-05-27
I've dug around for a while now and can't figure this out. I have a System Snapshot script I put together and everything works fine except the saving of my iptables setup via iptables-save. I execute the script via sudo and the ultimate goal would be to run in regularly through cron. Here is what I have:

```

BKDIR=/(backup dir)/$(date +%F)
mkdir $BKDIR
chown -R myusername:myusername $BKDIR
dpkg --get-selections > $BKDIR/Package.list
cp /etc/apt/sources.list $BKDIR/sources.list
apt-key exportall > $BKDIR/Repo.keys
tar czf $BKDIR/etc.tar.gz /etc/
cp /etc/iptables.rules $BKDIR
/sbin/iptables-save > $BKBIR/livefirewall.conf

```

everything works except the iptables-save line. I've tried the following variations:
```
iptables-save | tee $BKBIR/livefirewall.conf
sh -c "iptables-save > $BKBIR/livefirewall.conf"
bash -c "iptables-save > $BKBIR/livefirewall.conf"
```

All these commands work if I execute with sudo but will now work inside the script. The chown was an attempt to give the output redirect access.

The /etc/iptables.rules is created with the following script on if-post-down I grabbed from ubuntu wiki I think, works fine
```

#!/bin/sh
iptables-save -c > /etc/iptables.rules
if [ -f /etc/iptables.downrules ]; then
   iptables-restore < /etc/iptables.downrules
fi
exit 0

```

Any help would be appreciated.

---

