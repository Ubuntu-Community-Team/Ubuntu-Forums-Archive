---
title: "Democracy  on feisty"
date: 2007-06-05
forum: Multimedia &amp; Video
---

### Post by khateeb on 2007-06-05
Hi all

I am trying to install Democracy player on Feisty. I added the repository the Democracy site recommended but I am still getting error in Synaptic:

democracyplayer:
  Depends: python (<2.5) but 2.5.1-0ubuntu3 is to be installed
 Depends: mozilla-dev  but it is not installable
 Depends: mozilla-psm  but it is not installable

I can't find Mozilla browser or any of its components (they were installed automatically in edgy). And I am not really sure what the problem with Python is.

Please help

---

### Post by fluoblack on 2007-06-05
It seems like a conflict with your repositories. If you don't mind installing a non bleeding-edge democracy player, remove the democracy repo and install democracyplayer which is already present in the default Ubuntu repositories.

```
sudo apt-get install democracyplayer
```

---

### Post by khateeb on 2007-06-05
Thanks

it is working now

:D

---

### Post by RAdams on 2007-06-06
That fixed it for me too.

---

### Post by SLA_leandrin on 2007-06-22
I've made the install "sudo apt-get install democracyplayer"

but still not working:

> Traceback (most recent call last):
  File "/usr/bin/democracyplayer.real", line 21, in <module>
    import gtcache
  File "/var/lib/python-support/python2.5/democracy/gtcache.py", line 5, in <mod        ule>
    import config
  File "/var/lib/python-support/python2.5/democracy/config.py", line 9, in <modu        le>
    import platformcfg
  File "/var/lib/python-support/python2.5/democracy/platformcfg.py", line 20, in         <module>
    import gconf
ImportError: No module named gconf


Any ideas?

---

### Post by frtegularius on 2007-07-01
sometimes using aptitude rather than apt-get; try back if it doesn't wok.

---

