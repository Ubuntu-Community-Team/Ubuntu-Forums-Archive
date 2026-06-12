---
title: "Edit proxy settings using terminal/cronjob"
date: 2010-01-25
forum: Networking &amp; Wireless
---

### Post by tjallingk on 2010-01-25
How can I edit the system proxy setting using the terminal? Which file contains this settings? I want to edit this automatically using cronjobs, cause from 8-5 I need to use a proxy, but at home I don't need the proxy. How do I fix this?

---

### Post by chewearn on 2010-01-26
Gnome proxy settings are store in gconf, under: /system/proxy

To change the settings in a BASH script, use "gconftool-2" command. E.g.

1. change proxy mode to "auto" (turn proxy on)
```
gconftool-2 -s -t string /system/proxy/mode auto
```

2. change proxy mode to "none" (turn proxy off)
```
gconftool-2 -s -t string /system/proxy/mode none
```

You can then use crontab to run the script at the appropriate time.

---

### Post by satish.iith on 2010-02-14
it's okay to turn it on or off
but how can i enter the http proxy in terminal and i really don't know much about gconf....
btw iam using ubuntu 9.04
please help me..

---

### Post by chewearn on 2010-02-14
> **satish.iith said:**
> it's okay to turn it on or off
but how can i enter the http proxy in terminal and i really don't know much about gconf....
btw iam using ubuntu 9.04
please help me..

Well, you could enter the proxy manually via GUI.  You only need to do this once; after that, turn on/off switch via command line.

Else, learn about gconf command line manipulation:
```
man gconftool-2
```

---

