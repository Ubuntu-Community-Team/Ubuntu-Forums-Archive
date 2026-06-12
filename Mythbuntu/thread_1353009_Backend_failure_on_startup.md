---
title: "Backend failure on startup?"
date: 2009-12-12
forum: Mythbuntu
---

### Post by epi 1:10,000 on 2009-12-12
mythbuntu 9.04 x86_64 w/ avenard .22

My backend fails on startup  with the folowing log:

2009-12-12 08:21:10.659 mythbackend version: branches/release-0-22-fixes [22952] [www.mythtv.org]("http://www.mythtv.org")
2009-12-12 08:21:10.705 Using runtime prefix = /usr
2009-12-12 08:21:10.735 Using configuration directory = /home/mythtv/.mythtv
2009-12-12 08:21:10.828 Empty LocalHostName.
2009-12-12 08:21:10.873 Using localhost value of hall-dvr
2009-12-12 08:21:10.893 Testing network connectivity to '192.168.24.97'
2009-12-12 08:21:10.998 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2009-12-12 08:21:11.068 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
SSDP::PerformSearch - did not write entire buffer.
SSDP::PerformSearch - did not write entire buffer.
....2009-12-12 08:21:11.198 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
............................................................................
2009-12-12 08:21:13.117 UPnPautoconf() - No UPnP backends found
2009-12-12 08:21:13.131 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2009-12-12 08:21:13.135 Deleting UPnP client...
2009-12-12 08:21:13.135 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2009-12-12 08:21:14.125 Failed to init MythContext, exiting.


How do I configure the Database conection???  Can anyone see any other problems?

---

### Post by SiHa on 2009-12-12
I think your backend is starting up before you have an IP address. Have a look at [[COLOR="Blue"]_this_[/COLOR]](http://ubuntuforums.org/showthread.php?t=1310458&highlight=IP_ADD_MEMBERSHIP) thread.

---

### Post by epi 1:10,000 on 2010-01-08
I tried the instructions on your link to no avail.

Problem was resolved on w/ a fresh installation of mytbuntu 9.04 and updating to .22 w/ mythbuntu repos and then adding Avenard repos.  I fail to read his instructions fully the first install.

---

