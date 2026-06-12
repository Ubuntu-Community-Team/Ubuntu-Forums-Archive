---
title: "WPC54g ver 4 Wireless Problem Solved!!!"
date: 2009-03-26
forum: Networking &amp; Wireless
---

### Post by swalsh84 on 2009-03-26
I have the above card and after searching tonight for about 3 hours I finally solved the problem.  I have been back and forth with this card and trying to make it work with Ubuntu.  Here's what I learned:

[This thread]("http://ubuntuforums.org/showthread.php?t=133492") helped out a bunch because I was trying to use the Linksys drivers instead of the INPROCOMM IPN2220 drivers.  I had the 17fe:2220 portion correct, but not the right set of drivers.

That eventually solved the problem.

The [NDISWrapper Archive list]("http://web.archive.org/web/20080113194857/ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/") helped out in locating the [correct driver]("http://web.archive.org/web/20080125083634/ftp://ftp.support.acer-euro.com/notebook/aspire_1670/driver/80211bg.zip")

I hope that helps someone out there with this card.  I gathered enough information from the other cards to determine what I was looking for.  I'm pumped. :grin:

---

