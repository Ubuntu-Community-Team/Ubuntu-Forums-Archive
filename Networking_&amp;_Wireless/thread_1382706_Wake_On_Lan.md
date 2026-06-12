---
title: "Wake On Lan"
date: 2010-01-16
forum: Networking &amp; Wireless
---

### Post by NiGhtMarEs0nWax on 2010-01-16
I Was wondering if there was a proper solution to using wake on lan.

The solution i used before was startup script..

```
#!/bin/bash
while [ 6 -lt 9 ]; do
wakeonlan -i 192.168.1.3 AA:BB:CC:DD:EE:FF

sleep 60
done
```

The problem there is my system ceases to shutdown properly. because i cant seem to get it to run under run levels 2-5 only; default option is 0-6.

but on top of that it seems to break things, mainly VirtualBox. there is a virtualbox-ose startup script in init.d, also a halt and reboot script. im new to Linux, is this related?


so the problem i face now is finding an alternative, because my Buffalo Linkstation NAS requires a magic packet every 1 or 2 minutes or so, so i will need to find a solution that fits the requirements, but that isn't a shell script that runs indefinitely and interferes with my systems normal operations.

Thanks in advance.

---

### Post by NiGhtMarEs0nWax on 2010-01-16
i setup a cron job. it turns out startup scripts are run one after the other, the script i posted was looping indefinately and causing problems.


info on using crontab found [here]("http://www.unixgeeks.org/security/newbie/unix/cron-1.html") for anyone using the forum search.


Thanks!

---

