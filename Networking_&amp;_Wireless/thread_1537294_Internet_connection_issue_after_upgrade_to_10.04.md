---
title: "Internet connection issue after upgrade to 10.04"
date: 2010-07-23
forum: Networking &amp; Wireless
---

### Post by Phoenix87 on 2010-07-23
Hallo there.

I think I'm going to report an old and common issue, that showed up in the last days to me, when I managed to update my two 9.10 (one wired desktop and one wireless laptop, the both of them connected to a router). They worked just fine before the upgrade, but after it, they were both affected by the very same problem, which i'll describe here: internet connection seems to work fine, because I can ping, say, google.com and other sites. I can download and install packages from repos, apply upgrades. But Firefox and some other applications won't connect. Searching the internet I've found a solution for the web browser (disableIPv6 = true), but the problem with other applications remained. Then following some other threads I completely disabled IPv6 (by editing sysctl.conf, rc.local,...), but the problem is still there.

Playing with my router's MTU value i discovered that if I set it to 1492 then firefox works well, otherwise if i set it to 1500 firefox won't load anything.

Within another LAN, i installed a 10.04 from scratch on a netbook, and everything worked fine. Therefore I tried a live version of 10.04 on the previously mentioned machines, but the same issue showed up. All these elements leads me to think that the problem might be the router, but I don't know which settings would do the trick. Also, everything worked fine before the upgrade, and I have not changed anything in the configuration page of my router.

Thank you in advance for your replies!

Best regards!

Gab.

---

### Post by Phoenix87 on 2010-07-26
So here is an actual example of what's happening:

I tried to commit changes towards a code repository on googlecode with RabbitVCS, but the process failed because RabbitVCS wasn't able to access googlecode.com. Then I visited the repository with Firefox (disableIPv6 to true) and I saw the files that were there already and everything. After all these operations I attempted to commit changes again with RabbitVCS, and this time everything went fine, files were uploaded correctly.

Any clues?

Thanks!

---

### Post by Phoenix87 on 2010-07-28
Same problem with wget. When I try to download something with wget, it hangs untill timeout.

---

### Post by Phoenix87 on 2010-08-03
Finally I've found a solution. I edited my /etc/hosts file. Before it looked like

```
127.0.0.1	localhost
127.0.1.1	phoenix-zd7000

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

but since I have completely disable IPv6 on my machines, i removed the ip6-related lines, i.e. I ended with

```
127.0.0.1	localhost
127.0.1.1	phoenix-zd7000
```

After reboot every application that connects to the internet works fine.

IMO this problem is related to a residual configuration when passing to 10.04 from a previous version. I think that this solution I've outlined here is not the best and clean solution, because I had to disable IPv6, whereas the previous versions of ubuntu worked fine even with enabled support for IPv6 protocol. Therefore I don't know whether I should mark this thread as [SOLVED]. I'd say this issue is [partly/SOLVED].

Please provide an answer to this thread!!

---

