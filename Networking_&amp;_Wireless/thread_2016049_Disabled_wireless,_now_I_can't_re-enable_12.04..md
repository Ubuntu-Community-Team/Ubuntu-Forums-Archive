---
title: "Disabled wireless, now I can't re-enable 12.04."
date: 2012-07-04
forum: Networking &amp; Wireless
---

### Post by RKyle on 2012-07-04
Hi, I disabled wireless through the drop down menu that appears when you click the wireless icon and now there is no option for wireless and I can't re-enable it. It's a Broadcom device that did need a restricted driver but I looked in the restricted drivers to see of it would be there like before and it wasn't.

---

### Post by madvinegar on 2012-07-04
Try this.
Open terminal and write

```
sudo rfkill unblock all
```

---

### Post by RKyle on 2012-07-04
Thanks!

---

### Post by haplorrhine on 2012-08-14
I have a similar problem, but that command line didn't work.

It's also a Broadcom Wifi device (BCM4313).  It has worked for the last few weeks.  I have disabled it using the keyboard before, but it didn't come back on this time.  The command line *sudo lshw -C network* gives the output **-network DISABLED*.  Only my wifi, not my ethernet, says *DISABLED*.  The drop-down menu has *Enable Wireless* checked.

I was disabling it to compare battery usage under two different session types with wifi off.  One is a custom session that only runs LibreOffice on startup.

---

It's working again.  I tried restarting a few times without improvement.  After I shut down my Aspire One (AO) 722 for the night and powered it back up in the morning, I had wifi again.  Maybe it needed a shut down, not just a restart.

---

### Post by Feathers McGraw on 2013-05-18
> **madvinegar said:**
> Try this.
Open terminal and write

```
sudo rfkill unblock all
```


Many thanks, this just solved the same problem for me.

Out of interest, can I ask if you know what exactly happened to cause the problem and what this command does to solve it?

Feathers

---

