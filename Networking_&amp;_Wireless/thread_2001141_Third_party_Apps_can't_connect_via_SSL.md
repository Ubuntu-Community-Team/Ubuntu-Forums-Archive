---
title: "Third party Apps can't connect via SSL?"
date: 2012-06-10
forum: Networking &amp; Wireless
---

### Post by crunchie812 on 2012-06-10
I have several proprietary applications which require authentication via the Internet:  Pianoteq Play native Linux version, and Native Instruments Kontakt Player, and OnlineSheetMusic Viewer running under Wine. There was no problem with this until I upgraded to 12.04.  After upgrading my processor and memory these programs required re-activation, and reported that they could not connect to the internet. For Pianoteq and Kontakt, they offered a workaround obtaining a key from the web sites and pasting it in. There is no such workaround for the OnlineSheetMusic viewer, which requires a connection to reload my sheet music.  It reports this error:
  "Online Sheet Music Viewer 8.2.2.0 : Viewer could not connect to the web site. Please make sure your firewall settings and your Internet Options Control Panel settings allow the Viewer application to connect to gateway.onlinesheetmusic.com:443."

I am not running a firewall other than the minimal one one my router, and those settings have not changed.

At first I thought it was a Wine problem, but since the Linux version of Pianoteq has the same problem, it seems to be a system problem. Anyone have any idea what could be causing this?

---

### Post by crunchie812 on 2012-10-01
Bug has been fixed through some update, not sure when...

---

