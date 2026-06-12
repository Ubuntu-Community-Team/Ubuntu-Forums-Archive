---
title: "Wifi keeps disconnecting"
date: 2010-11-11
forum: Networking &amp; Wireless
---

### Post by sdmike6 on 2010-11-11
I'm running Ubuntu 10.04 64bit on a 15' Dell Studio

After doing an update my internal wireless will not connect to my wireless network.

The card is on, I can see networks around me, but it will not connect to mine. It just acts like its connecting and then disconnects.

What steps should I take to resolve this?

---

### Post by theSuperman on 2010-11-11
While it keeps disconnecting, open up the log files. Go to System->Administration->Log File Viewer. Keep an eye on Dmesg and Syslog (maybe Messages too) and post what you see in there.

---

### Post by sdmike6 on 2010-11-11
Those are to huge to post.

I looked around the forum more and people have been having problems when switching to Ubuntu 10.10 or when they did a kernel upgrade. 

Was there a recent kernel upgrade that is making my wifi acting weird?

---

### Post by theSuperman on 2010-11-11
Only post the relevent lines that have to deal with networking (like NetworkManager or wpa_supplicant).  There wouldnt be any Proprietary drivers to install, would there? Try System->Administration->Additional Drivers.

---

### Post by sdmike6 on 2010-11-12
I rolled back to the previous kernel and now my wifi works.

---

