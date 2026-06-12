---
title: "GKrellM help"
date: 2010-10-30
forum: Networking &amp; Wireless
---

### Post by ozzynotwood on 2010-10-30
Can somebody please educate me on GKrellM?

I set it up using the $O format string to display cumulative download and upload for then month, but the problem is the meter resets itself after I close the program down, I need this program to log my internet usage over then whole month.

What am I doing wrong?GKrellM help

---

### Post by elico on 2010-10-30
for what do you need it?
you can try NTOP.

---

### Post by nah40 on 2010-10-30
try Network Traffic Manager (NTM).
Get it from Sourceforge

---

### Post by ozzynotwood on 2010-10-30
> **elico said:**
> for what do you need it?
you can try NTOP.


"I need this program to log my internet usage over then whole month"

---

### Post by ozzynotwood on 2010-10-30
Look at both of those, one was for Unix, the other had 404 errors, does anyone know if a download + upload meter that will record my internet usage over the whole month (link Netmeter for windows, which i cant even run under wine)

---

### Post by genterminl on 2011-01-22
Did you ever find anything that does what you want?  I suspect you may have to roll your own.  Most of the tools mentioned already show current usage, and maybe cumulative usage while they are running.  What you probably need is to create some scripts to be run by cron which check usage every five minutes (just for example) and then maintain your own cumulative totals.

---

### Post by ozzynotwood on 2011-01-23
Using Gkrellm, got it working, and resets once a month like I want it to.

---

