---
title: "Uganda Orange Mobile Broadband w/ Huawei E1752 Modem"
date: 2012-11-26
forum: Networking &amp; Wireless
---

### Post by guardsman85 on 2012-11-26
I'm writing this post, even though it is "SOLVED" before I write it in hopes that someone else looking for an answer will be able to save some time.  It took lots of searching, and gathering information from different sources (unfortunately, I didn't keep a list) to put together the solution.  This is intended to be a summary for "the next guy" to use.

Problem:  I could not get a connection on Orange Uganda's mobile broadband network using a Huawei E1752 USB modem.  I am running Ubuntu 12.10.

Solution:

1. Download and run the full version Sakis3G script from [sakis3g.org]("http://www.sakis3g.org/#download")
```
wget "[http://www.sakis3g.org/versions/latest/i386/sakis3g.gz](http://www.sakis3g.org/versions/latest/i386/sakis3g.gz)"
echo "dda70fd95fb952dbb979af88790d3f6e  sakis3g.gz" | md5sum -c
gunzip sakis3g.gz
chmod +x sakis3g
./sakis3g --interactive
```2.  Select "Connect with 3G" from the menu.  Your modem should be detected, and prepared for use.

3.  If prompted, enter the following values:
APN:  orange.ug
Username:  orange
Password:  orange

4. At this point the connection should be established.  To monitor data usage, select the "Connection information" option from the menu.  Select "Disconnect" to disconnect the connection.

Hopefully this is helpful to someone else out there!

---

### Post by isaac890 on 2013-03-12
Hi. Thank you for your post. I have been struggling trying to make this work. I wonder though, if my modem is unlocked, how do i connect using another service provider, say Airtel?

---

### Post by isaac890 on 2013-03-12
> **isaac890 said:**
> Hi. Thank you for your post. I have been struggling trying to make this work. I wonder though, if my modem is unlocked, how do i connect using another service provider, say Airtel?


Never mind, just did and it was simple. Just used custom apn and that was it.

---

