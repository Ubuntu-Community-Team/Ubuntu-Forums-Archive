---
title: "Internet slow after upgrade to kernel 2.6.32-24"
date: 2010-07-27
forum: Networking &amp; Wireless
---

### Post by Malcy on 2010-07-27
I have just built a PC based around an i7-860 and Asus P7P55D mobo. It was running fine until the big update that happened today and now the internet is like treacle. I did the same update to my other (different hardware) PC and all is fine with it.

When I load the earlier 2.6.32-21 kernel instead of 2.6.32-24, the new system works as it should and the Internet is very fast. This suggests to me that the kernel update is the problem, most likely the NIC driver. This motherboard has a Realtek 8112L NIC fitted.

Has anyone else had this issue and what is the best way around it other than loading the older kernel and hoping that the next update will fix it?

---

### Post by Malcy on 2010-07-28
Anyone?

---

### Post by fingaz on 2010-07-28
Three things I can suggest really, baring in mind that the kernel that you mention is 'regression' grade (ie. testing):

1. File a bug report. (See [https://help.ubuntu.com/community/ReportingBugs]("https://help.ubuntu.com/community/ReportingBugs"))

2. Roll back to previous kernel!

3. Try and locate where the bottle-neck is; if it's slowness caused by CPU time, what app is causing the excess load? Purge and reinstall that particular app perhaps. If it is definately the connectivity speed (Try speedtest.net) then maybe take a look at updating the module/drive for this particular NIC?

Out of interest, did you run "apt-get upgrade" to get this? Or through the update manager GUI? Although i prefer command line; the GUI is better for stability, in the sense that it doesn't display grade 4 + 5 updates by default! Much safer (from a stability point of view anyway!)  :)

---

### Post by Malcy on 2010-07-28
Thanks for the reply.

1. I would like to file a bug report but I need to have a better idea of where the problem is other than the Internet slowing down.

2. I have rolled back to the previous kernel which restores the Internet connection speed but I don't see this as a long term solution.

3. This is what I need to do for (1) but I haven't been able to narrow it down yet. Of five computers here, all of which have Ubuntu 10.04 and the latest upgrades on them, this is the only one with an issue to do with the Internet slowing down. I'll spend more time looking but if rolling back the kernel resolves things, then is the problem due to a change made to the kernel? I can't find the Realtek 8112L NIC drivers separately to upgrade/downgrade them.

p.s. I used update manager on this occasion.

---

