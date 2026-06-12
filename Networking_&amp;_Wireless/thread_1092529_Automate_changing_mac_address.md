---
title: "Automate changing mac address"
date: 2009-03-10
forum: Networking &amp; Wireless
---

### Post by jreiner3 on 2009-03-10
I wanted to automate changing the mac address on eth0 and I could not find any information online so I figured it out and thought I'd post it to the forum, hopefully it helps someone else. 

After installing macchanger add the following line in the process_options method of /etc/init.d/networking 

```
macchanger -a eth0 
```

here's the whole new method

```
process_options() {
    macchanger -a eth0
    [ -e /etc/network/options ] || return 0
    log_warning_msg "/etc/network/options still exists and it will be IGNORED! Read README.Debian of netbase."
}
```

process_image is called any time networking is started or restarted thus ensuring a "fresh" mac address each time.

---

### Post by wannadumpwindows on 2009-03-10
Nice job.

I've been trying to figure this out for a little while now. I could never get a simple script to work properly.

---

