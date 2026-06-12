---
title: "Natty broke my hostapd"
date: 2011-05-04
forum: Networking &amp; Wireless
---

### Post by emunson on 2011-05-04
I use an Atheros AR922X wireless card in my router/access point and everything was working fine under maverick.  Now when I try and start hostapd I get this:


```

root@puffin:~# hostapd -d /etc/hostapd/hostapd.conf
Configuration file: /etc/hostapd/hostapd.conf
ctrl_inerface_group=0
Failed to create interface mon.wlan0.
nl80211 driver initialization failed.
wlan0: Unable to setup interface.
rmdir[ctrl_interface]: No such file or directory

```

Google is not helping, the only relevant hit is a thread where the poster fixed the problem but did not say how.

---

### Post by emunson on 2011-05-05
Bump

---

### Post by Cheesehead on 2011-05-05
Is the nl80211 driver included with the update? Or do you need to install it separately?

Is the driver installed...is it showing in /sys/modules?

---

### Post by emunson on 2011-05-05
I don't think that is a kernel driver, it was part of the hostapd binary in maverick.

---

### Post by emunson on 2011-05-05
Bump

---

### Post by emunson on 2011-05-06
bump

---

### Post by Cheesehead on 2011-05-06
Stop bumping.
It's not helping because you are not providing enough information.

If you believe that your wi-fi hardware driver does not need to be updated, then why do you think you are getting an error message that tells you that your wi-fi hardware driver needs to be updated?

Have you looked in syslog or (hint, hint) dmesg for additional information?


---------------------------

EDIT:

Wow. 
Upon reflection, that was very inappropriate of me to write.
And a very mean way to express it.
This post was not helpful at all.

My apologies.

---

### Post by emunson on 2011-05-06
I bump because in my experience with the ubuntu fora, if your post isn't on the first page, it isn't being read and certainly isn't being answered.  Also, this isn't the way I would approach someone asking for help, generally if I need more information I ask for it, I certainly don't ignore the post and then get snarky about not providing enough info. </rant>

The error posted above is all I get from the system.  dmesg/syslog show that everything is great from the kernel perspective.  If I am reading the docs correctly, the nl80211 driver is part of the hostapd package and is the interface to all mac80211 based wireless drivers in kernel.  It is the upgrade that broke my setup, I am running the latest out of the Natty repo.

---

### Post by emunson on 2011-05-08
Bump

---

### Post by paoletto on 2011-07-12
same problem here

bump!

---

### Post by emunson on 2011-07-12
paoletto:

I am not sure what fixed it, but I no longer have this problem.

---

### Post by emunson on 2011-07-13
Part of what has changed is I no longer start hostapd on boot, it is started by my br0 script.  Not sure if that mad the difference, but you might try starting hostapd by hand and see if it comes up.

---

