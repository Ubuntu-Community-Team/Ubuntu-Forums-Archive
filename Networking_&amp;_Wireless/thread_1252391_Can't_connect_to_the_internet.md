---
title: "Can't connect to the internet"
date: 2009-08-28
forum: Networking &amp; Wireless
---

### Post by davbeck on 2009-08-28
I am using Ubuntu 9.04 (just installed) and I have it connected via ethernet cable to my Mac which has internet sharing enabled.

The network icon shows the appropriate connection and all seams to work. However, when I try to view a webpage, say Google or anything except [http://start.ubuntu.com/9.04/](http://start.ubuntu.com/9.04/), Firefox just sits there drooling on itself. Similar situation in Update Manager.

The weird thing is that when I open up the terminal, I can ping Google.com just fine, I can use wget to download the Google webpage just fine.

---

### Post by doas777 on 2009-08-28
do you have any proxy settings in firefox?
I assume you pinged google by name, not IP right? Otherwise i would suspect an DNS issue. 

what does the FF status bar say when it's sitting there spinning?

---

### Post by davbeck on 2009-08-28
Yes I pinged it by name.

The status just says "Done" even though the spinner is still going.

---

### Post by doas777 on 2009-08-28
hmmmm. the issue is likely either with firefox or with the ics on the mac. I wonder if installing a socks proxy on it might be a simple enough proposition. proxies are usually easy. I don't do macs so can't help there.

have you tried resetting ff to defaults?

---

### Post by davbeck on 2009-08-28
I just plugged the machine directly into the router and had the exact same problem. I am not sure how you would reset Firefox but it is brand new install. I haven't changed anything.

---

### Post by davbeck on 2009-08-28
Also, it's not just Firefox. Update Manager, Add/Remove software and Evolution Mail all have the same problem.

They aren't timing out or anything they just sit there loading never actually making progress.

---

