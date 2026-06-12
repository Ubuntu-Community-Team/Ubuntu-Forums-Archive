---
title: "Unable to mount location"
date: 2010-01-11
forum: Networking &amp; Wireless
---

### Post by gdonwallace on 2010-01-11
This is the same error that has been posted before, but I have a slightly different issue.

I will preface this by saying that we are running DHCP, except that my machine has a static IP address so I can ssh from my laptop if I am out of the office and need to work on the network.

I am running Ubuntu on my office machine.  I believe it was in 8.04 that I was able to view the windows shares that we have setup.  However starting in 9.04 it was not able too, and started getting the error message about unable to retrieve share list from server.

I have followed all the how-to's and even reinstalled Samba to no avail.  Still getting this message.  

The strange parts are these:
   1.  I run **smbtree** in terminal and I can see everything, all network shares including printers and other machines...no problems.

   2.  I have virtual-box installed on this same machine with windows XP and am able to see the windows shares just fine.  Can read / write to them with no problem.  I even have a samba share setup on a local guest directory for virtualized XP to access, and I can do that with no problems.

I am a little perplexed as to what can be going on. It is obvious that samba is working, but for some reason I can't see anything through Nautilus.

Any suggestions?

---

