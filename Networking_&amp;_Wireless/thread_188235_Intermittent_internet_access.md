---
title: "Intermittent internet access"
date: 2006-06-03
forum: Networking &amp; Wireless
---

### Post by challah on 2006-06-03
Hi.  New to Ubuntu but medium savvy on computers generally.

Had odd problem after 6.06 install: after launching Firefox, I could get to the the "Getting Started" link ([http://www.mozilla.com/firefox/central/](http://www.mozilla.com/firefox/central/)) and about every third try I got to the bookmarked Ubuntu page.  No Google, no Wiki, nothing else.

Messed around in networking for eth0 and found that autoinstall set up my router internal address, 192.168.0.1 as primary DNS server, which didn't seem right.

I got into the admin page for the ADSL router and found the two DNS addresses.  Deleted the primary 192.168.0.1 and added in the one from the ADSL router.   Now I have reliable internet access.

Cheers!

---

