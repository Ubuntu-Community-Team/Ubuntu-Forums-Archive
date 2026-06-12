---
title: "intrepid server losing connectivity every 20 minutes"
date: 2008-12-10
forum: Networking &amp; Wireless
---

### Post by Tidder on 2008-12-10
I have a very strange issue here.  I've freshly loaded Intrepid Server onto a file server consisting of an Intel D945GCLF2 motherboard, 2xSeagate 500gb hdds.  I'm using the onboard nic which is a realtek pci-e gigbit adapter (RTL8111B I believe).  I started off having 2 issues.

First issue:  packet dropping.  Fixed by downloading and installing drivers from realteks website instead of using the (incorrect) driver r8139 that ubuntu autodetected.

Second issue: The server is losing network connectivity every 20 minutes.  I'm hosting some NFS shares on this machine, to an ESXi server.  The ESXi server shows that the NFS share is dropping and becoming inactive.  I have now watched it drop about 4 times in a row, and it's almost 20 minutes exactly.

Now here's the strange kicker.  If I ping anything from my ubuntu server, the connections to it become active again.  ESXi sees the NFS share once again, and everything is ok.  I've currently worked around the problem by setting up a cron job to ping google.com every 10 minutes.  Isn't that strange?? I've looked around for maybe power saving or something... cron jobs, etc.  I've found nothing that could be pointed out as the problem.

Thanks in advance for any help/advice/guidance!

---

### Post by Tidder on 2008-12-12
bump + 1

---

### Post by Tidder on 2008-12-20
hop, skip and a bump

---

### Post by Tidder on 2008-12-28
Well, last bump before I give up on yet another failed attempt to get help from the community.  Perhaps I should try going back to hardy?

---

