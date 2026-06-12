---
title: "firefox 5 and ed2k system-wide handling"
date: 2011-06-17
forum: Networking &amp; Wireless
---

### Post by magowiz82 on 2011-06-17
Hi,
I'm trying to set up firefox system-wide to handle ed2k links properly, I'm following amule wiki howto at this page [http://wiki.amule.org/index.php/Ed2k_links_handling](http://wiki.amule.org/index.php/Ed2k_links_handling)  but it seems a little outdated, I tried to create  /usr/share/firefox/greprefs/all.js and   /usr/local/share/firefox/greprefs/all.js but I got no results. I also  tried to edit /usr/lib/xulrunner-1.9.2.17/greprefs/all.js
 with no luck. So where should I put ed2k handling strings to apply them system-wide ?

---

### Post by magowiz82 on 2011-06-17
I found the file I was looking for : /usr/lib/firefox-5.0/defaults/pref/syspref.js

---

