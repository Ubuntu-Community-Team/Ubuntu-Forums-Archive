---
title: "Problem with local domains 11.04"
date: 2011-05-03
forum: Networking &amp; Wireless
---

### Post by Rb33 on 2011-05-03
Hi,

After upgrading to Ubuntu 11.04, I cannot use .local domains in my webrowser.

I can ping the local hostnames if I only write the hostname, but it doesn't work if I use hostname.domain.local.

I guess that avahi is the problem, but I don't know where to start.

UPDATE:

It works after running:
sudo /etc/init.d/avahi-daemon stop
service avahi-daemon start

The output of the last command is:
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.52" (uid=1000 pid=3248 comm="start avahi-daemon ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))

But now it works. Anyone know a permanent solution?

---

### Post by gamblor87 on 2011-05-05
Having the exact same problem. Not at home so can't try on my server but will do soon.

That error message is a permissions error I think. I don't know if the service even started? Odd!

---

