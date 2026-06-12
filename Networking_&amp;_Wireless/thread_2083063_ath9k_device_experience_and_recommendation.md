---
title: "ath9k device experience and recommendation"
date: 2012-11-11
forum: Networking &amp; Wireless
---

### Post by kurt18947 on 2012-11-11
I've been using a Netgear WNA1100 for probably 2.5 years.  I've recommended it as plug 'n' play which it is.  Starting with the 12.xx versions, I'd get fluctating signal levels and occasional disconnects.  Removing the ath9k connection and installing an RTL-8192SU device worked well, no signal strength fluctuation or disconnects.  After reading a thread here, I created the following file:

```
/etc/modprobe.d/ath9k.conf
```The contents of that file are one line:

```
options nohwcrypt=1

```This seems to have helped.   I haven't had a disconnect in serveral hours usage.  Signal strength is still not as strong as the smaller RTL-8192SU device but the ath9k device works fine.

---

### Post by wildmanne39 on 2012-11-11
Hi, that option normally fixes the issues with ath9k.

RTL-8192SU usually has its own set of issues that have to be resolved.

---

### Post by chili555 on 2012-11-11
I believe the file should read:```
options [COLOR="Red"]ath9k[/COLOR] nohwcrypt=1
```

---

### Post by wildmanne39 on 2012-11-11
Thanks chili555 I missed that part I was doing to many things at once.

---

### Post by kurt18947 on 2012-11-12
> **Wild Man said:**
> Hi, that option normally fixes the issues with ath9k.

RTL-8192SU usually has its own set of issues that have to be resolved.

Oops, I'll have to go back and look at my cheat sheet.  My experience with recent releases and RTL-8192SU have been pretty much trouble free.  The only thing I've run into recently  is the 'suspend-resume-no wireless network' glitch.  The fix - thanks Chili 555 - is a one line file to disconnect the wireless network prior to suspending.  Then it resumes correctly.

---

### Post by ahallubuntu on 2012-11-12
These Realtek chipsets with similar names are not exactly the same - but my 8192CU (mini USB dongle) deso not work out of the box reliably on 12.04 or 12.10.  They SORT of work, but they won't reliably connect.  (I originally though it worked in 12.04 but not reliably.) Building the latest driver from Realtek's website does fix the problem, though; I've had no other  noticeable issues with that Realtek driver.

---

### Post by kurt18947 on 2012-11-13
> **ahallubuntu said:**
> These Realtek chipsets with similar names are not exactly the same - but my 8192CU (mini USB dongle) deso not work out of the box reliably on 12.04 or 12.10.  They SORT of work, but they won't reliably connect.  (I originally though it worked in 12.04 but not reliably.) Building the latest driver from Realtek's website does fix the problem, though; I've had no other  noticeable issues with that Realtek driver.

I've had a similar experience with the 8192Cus.  The 'built-in' driver works but doesn't seem as fast or stable as the one from RealTek.

---

