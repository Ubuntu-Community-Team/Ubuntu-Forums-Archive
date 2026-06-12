---
title: "oident can bind 113 | guess its a bug"
date: 2010-09-08
forum: Networking &amp; Wireless
---

### Post by mR bluE on 2010-09-08
hi,
i am using ubuntu 10.04 on a AMD64 mashine.

so its the odientd version 2.0.8.-3
here's what i allready write at my bugreport at launchpad
my /etc/oident.conf
```
# Configuration for oidentd
# see oidentd.conf(5)
#
default {
 default {
  deny spoof
  deny spoof_all
  deny spoof_privport
  allow random
  allow random_numeric
  allow numeric
  deny hide
 }
}
 # you may want to hide root connections
user "root" {
 default {
  force reply "unknown"
 }
}
 user "tom" {
 default {
  force reply "ladidadi"
 }
}
 
```my /etc/default/oident
```

# options to use when starting oidentd as daemon:
# -m    lookup masquaraded connections in /etc/oidentd_masq.users
# -f    forward requests for masquaraded connections to real host
# -q    don't log connections to oidentd
# see oidentd(8) for detailed list
OIDENT_OPTIONS="-mf -d"
 # user / group
OIDENT_USER=oident
OIDENT_GROUP=oident
 # Allow the default router to act as an oidentd proxy? (yes/no)
# this is needed behind a masquarading router that runs oidentd -f
# if your identd proxy is not the default router, you have to
# manually specify it via -P
OIDENT_BEHIND_PROXY=yes

```
so here's the output in syslog after i startet it in the debug modus

```
Aug 18 17:37:54 lucid oidentd[2435]: [oidentd_
inet_util.c:79:setup_bind] DEBUG: bind: Address already in use
Aug 18 17:39:12 lucid oidentd[2441]: Connection from 192.168.0.5:46302
Aug 18 17:39:12 lucid oidentd[2441]: [192.168.0.5] Successful lookup: 53813 , 5253 : tom (ladidadi)

```
I've tried it in LAN and WAN and also with OIDENT_BEHIND_PROXY=no

 I also try the package from maverick (version 2.0.8-4), now i don't get the "adress allready in use" message in syslog, but it doesn't work at all, i just get a
> oidentd[3548]: [192.168.0.5] 54095 , 5253 : ERROR : NO-USER
i am pretty frustrated that no one on lauchpad intrested in this, the debian maintainer answerd in 24hr, but of course he could'nt help, cause ubuntu is not debian ;-).


Anyone uses this daemon here? Does it realy work on youre mashine's? If yes which config did you use? Or does anyone got a hint for me?


thx

---

