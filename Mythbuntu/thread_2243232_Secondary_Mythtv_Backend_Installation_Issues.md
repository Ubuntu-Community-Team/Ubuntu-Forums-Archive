---
title: "Secondary Mythtv Backend Installation Issues"
date: 2014-09-07
forum: Mythbuntu
---

### Post by sheetsb on 2014-09-07
I am new to mythbuntu and mythtv.  I installed my primary backend a few weeks ago and it is working well.  Last night I installed a secondary backend and I'm having issues.  When I look at the mythweb page on the primary it shows all the tuners, but those on the secondary show as not connected.  If I try to connect the mythweb on my secondary I get a series of mysql errors.  I tried running myth frontend on the secondary and when I look at the system status page it shows errors for the tuners on my secondary.

I'm not sure where to start troubleshooting this.  What logs do I need to review?  The tuners in both PCs are Hauppauge 2250s.  I installed the firmware on both.  The tuners are working on the primary and followed the same steps on the secondary.

---

### Post by sheetsb on 2014-09-07
I found my problem.  The host and password in the /etc/mythtv/config.xml file were both wrong.  I changed them to the settings for the primary backend and now the tuners show up as connected and idle.

---

