---
title: "HP Laserjet 4 Plus prints several HTTP headers and commands followed by blank pages"
date: 2012-08-30
forum: Networking &amp; Wireless
---

### Post by lsiden on 2012-08-30
Just sharing my experience for anyone that still has an old gray-scale HP Laserjet 4 Plus ("Old Faithful") or similar printer on a network interface and it started printing several mostly blank pages followed by what looks like an HTTP header followed by a single line of printer commands after you upgraded to 12.04:

[LIST=1]
[*]Get your stuff up-to-date.  For the heck of it, I purged then re-installed all the cups and hplip packages.
[*]Delete your printer/s.
[*]Open the printer setup dialog; tell it to scan for a printer on the IP address listed on your printer self-test page.
[*]When it finds it, select HPLIP for your connection.
[*]Select your driver.  Postscript (the recommended driver) is horribly slow.  Gutenprint is better, but I get the best results with hpcups PCL3.  It's fast and I can read a Google Map after I've printed it - which has become my de-facto printer test.
[/LIST]

If none of the above work, see [https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems)

*I'm too cheap to get a Mac and I'm sooo happy I don't have Windows!  :lolflag:*

---

