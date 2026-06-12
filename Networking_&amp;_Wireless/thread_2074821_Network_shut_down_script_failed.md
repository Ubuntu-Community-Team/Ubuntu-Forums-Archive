---
title: "Network shut down script failed"
date: 2012-10-22
forum: Networking &amp; Wireless
---

### Post by Brian Hartnell on 2012-10-22
I just upgraded from Ubuntu 11.10 to 12.04 then immediately upgraded again to 12.10. Everything went well with the upgrades and the system seems to work just fine. Not found anything that didn't work. The network was found and was able to get online with no problem obviously or I wouldn't have been able to update. After 12.10 was installed and I tried a bunch of programs, I shut the computer down and it came to an error screen after everything was closed. "Since the script you are attempting to invoke has been converted to an upstart job, you may also use the stop (8) utility , e.g. stop s35networking." Not sure why the shut down networking has failed, system will only shut down when you turn the power off, the screen doesn't go away until then. Is there an easy fix? Doesn't seem to affect anything other than it just doesn't completely power down when you tell it to.
Thanks
Brian H

---

### Post by nicocarbone on 2012-10-25
I am having the same problem since upgrading to 12.10. I still can't find the solution. If you find something, please post it. I'll do the same.

---

### Post by ORF1000 on 2012-11-14
I'm having the same problem.  Hope to find a solution soon.

---

### Post by zasq on 2012-11-17
I am having the same problem, but I can only see this text when trying to reboot... If this is a bug, to which package should it be reported, does anyone know?

---

### Post by antguada on 2012-11-23
I was having exactly the same problem and it looks like the reason was i didn't have a swap file or partition. Not sure i lost it.

You can create a swap partition or a swap file (which is probably easier).

Here you can find the instructions:

[https://help.ubuntu.com/community/SwapFaq]("https://help.ubuntu.com/community/SwapFaq")

[http://mce.commsbyte.com/index.php?option=com_content&view=article&id=81:ubuntu-swap-file-instead-of-partition&catid=10:linuxmce&Itemid=68]("http://mce.commsbyte.com/index.php?option=com_content&view=article&id=81:ubuntu-swap-file-instead-of-partition&catid=10:linuxmce&Itemid=68")

Hope that helps :-)

---

