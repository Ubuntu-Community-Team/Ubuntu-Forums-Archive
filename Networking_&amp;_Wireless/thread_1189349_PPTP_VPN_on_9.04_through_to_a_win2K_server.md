---
title: "PPTP VPN on 9.04 through to a win2K server"
date: 2009-06-16
forum: Networking &amp; Wireless
---

### Post by XturnLGod on 2009-06-16
Hi all,

For the past little while I had had trouble connecting with my HP laptop running Ubuntu 9.04 onto a network serving PPTP via a windows server. Every time I would get "could not connect" and nothing to clear as to why in the syslog...
I found it today, and thought I would share:

In the VPN connection's advanced settings, check off the "use point to point encryption" (MPPE). Once this was checked, my VPN connection was establised and worked fine.

hope this is of some help to someone.
XturnLGod

---

