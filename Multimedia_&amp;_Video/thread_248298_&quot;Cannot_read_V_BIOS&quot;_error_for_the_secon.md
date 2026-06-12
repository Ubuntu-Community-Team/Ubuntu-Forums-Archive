---
title: "&quot;Cannot read V_BIOS&quot; error for the secondary video card"
date: 2006-08-31
forum: Multimedia &amp; Video
---

### Post by intersteller_overdrive on 2006-08-31
I've been trying for awhile now to get dual monitors working under linux.  When I'm running windows I can use my computer's integrated graphics card (intel 82845G/GL) and a Nvidia GeForce4 mx4000 pci to have dual monitors.  I also know that both of these video cards will work independently in linux without any problems.  However, when I try to get them both working together I can't get anything on the second monitor.  In looking in my xorg.0.log the intel card driver is getting a "Cannot read V_BIOS" error and then the module is unloaded.  I can't figure out what the problem is because it works fine without the nvidia card installed.

In researching my problem I found that a patch was released for Suse Linux to address this same problem.  [https://bugzilla.novell.com/show_bug.cgi?id=171453&x=20&y=6&=Find]("https://bugzilla.novell.com/show_bug.cgi?id=171453&x=20&y=6&=Find")
Is there a patch for ubuntu or any possiblity of creating one?  Any help would be greatly appreciated.

>> [My xorg.0.log]("http://ttyfscker.pastebin.ca/156865")
>> [My xorg.conf]("http://ttyfscker.pastebin.ca/156868")

---

