---
title: "Mythbuntu 10.04 good except for lirc.conf"
date: 2010-04-01
forum: Mythbuntu
---

### Post by mike_r44 on 2010-04-01
Installed Mythbuntu 10.04 using a Hauppauge pvr-250 with no troubles last night. Did an update at the final stage where it hung forever trying to update lirc.conf.

---

### Post by superm1 on 2010-04-01
> **mike_r44 said:**
> Installed Mythbuntu 10.04 using a Hauppauge pvr-250 with no troubles last night. Did an update at the final stage where it hung forever trying to update lirc.conf.

Did it hang during install, or after install during MCC?

If during install, can you please try with one of the daily builds ([http://cdimages.ubuntu.com/mythbuntu/daily-live](http://cdimages.ubuntu.com/mythbuntu/daily-live))

If after install during MCC, can you reproduce this on a second try?

---

### Post by mike_r44 on 2010-04-01
Sorry but not sure what MMC is. I did a fresh install, configured the hauppauge pvr-250, configured schedules direct, mythfilldatabase, tested that tv and audio worked, then then an update where it hung forever around 95% done of updating the newly downloaded lirc.conf.

---

### Post by superm1 on 2010-04-01
> **mike_r44 said:**
> Sorry but not sure what MMC is. I did a fresh install, configured the hauppauge pvr-250, configured schedules direct, mythfilldatabase, tested that tv and audio worked, then then an update where it hung forever around 95% done of updating the newly downloaded lirc.conf.

Okay, so it was a post install type of thing.  Can you please file a bug using this command:

"ubuntu-bug lirc"

If there are any missing logs, we'll ask for them on the bug.

---

### Post by dschobel on 2010-05-16
Same issue here with the same card. The upgrade hosed lirc and trying to reconfigure with dpkg causes that to hang.

Trying apt-get purge / install lirc hangs at:

 2111 pts/1    Ss+    0:00 /usr/bin/dpkg --status-fd 32 --configure libftdi1 setserial lirc
 2133 pts/1    S+     0:00 /usr/bin/perl -w /usr/share/debconf/frontend /var/lib/dpkg/info/lirc.postinst configure 
 2139 pts/1    S+     0:00 /bin/sh /var/lib/dpkg/info/lirc.postinst configure

---

