---
title: "Nonexistent Samba servers still appear"
date: 2010-12-22
forum: Networking &amp; Wireless
---

### Post by fela on 2010-12-22
Hi
I'm running quite a few PCs in my house, one of them a Debian server which runs (amongst other things) a Samba server, which is configured as the master controller (I don't know whether this is significant to my problem though).

Recently I've acquired a new PC, as well as thrown a couple out. The problem is that the ones I've thrown out still appear in the network (when I browse it with windows or Ubuntu's file browser, not with findsmb however - that only shows machines that are on and it can connect to).

I'm almost certain that it's nothing to do with a 'network name cache' on the clients, as on the new PC the machines appear, even though there was never a time when both the new and old PCs were connected.

Could it be something to do with a config file or cache on the master controller server (whatever that means :D) ?

Cheers

---

### Post by fela on 2010-12-22
Just wanted to re-post saying I found the solution - I just restarted the samba server on domain master (ie. my home server) by going:

```
sudo /etc/init.d/samba restart
```

Can't believe this was bugging me for so long :o

Maybe I've gotten too used to Linux, and forgotten the old windows fable:

If it doesn't work, reboot it! :)

---

