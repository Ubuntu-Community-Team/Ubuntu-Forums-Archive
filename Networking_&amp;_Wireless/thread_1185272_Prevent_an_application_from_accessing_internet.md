---
title: "Prevent an application from accessing internet"
date: 2009-06-12
forum: Networking &amp; Wireless
---

### Post by ario on 2009-06-12
Hi
I wonder if I can prevent my new screensaver named electricsheep accessing internet. because it will download handreds of megabytes without any notice and I want to stop it or uninstall it:D
I searched google and found that All firewall softwares in linux used to block some special ports but not block a special software.
Any suggestions how to do that?
Thanks for your attention guys.

---

### Post by jimv on 2009-06-12
This might cause other issues with some websites, but if you block port 8080 it should also block ElectricSheep.

---

### Post by ario on 2009-06-13
Thanks you JIMV. But I think PORT 8080 is a useful port and blocking it may cause a lot of other softwares and webpages to malfunction. So I think this is not the right idea and not a permanent solution.

---

### Post by Barriehie on 2009-11-29
See my post [here](http://ubuntuforums.org/showthread.php?p=8411072#post8411072) regarding a solution.

Barrie

---

### Post by ario on 2009-11-29
Dude!
That was not what I want. That was all about deleting something like temprory files of such a software. I need block an special application like electric sheep software to access network.
By the way, Thanks for your attention.:)

---

### Post by Barriehie on 2009-11-30
What about hosts.deny?

Barrie

---

### Post by ario on 2009-11-30
Thanks Barriehie.
But the mentioned file will cause special domains to be blocked, but not special applications! I want a way to prevent special application to access internet.
For example:
Application A wants to access internet via website X.
Application B wants to access internet via some domain names like website X.
I only want to prevent application A to access the whole internet. I do not want to block website X because this will prevent Application B too.
Again thanks for your attention:)

---

### Post by Barriehie on 2009-12-01
> **ario said:**
> Thanks Barriehie.
But the mentioned file will cause special domains to be blocked, but not special applications! I want a way to prevent special application to access internet.
For example:
Application A wants to access internet via website X.
Application B wants to access internet via some domain names like website X.
I only want to prevent application A to access the whole internet. I do not want to block website X because this will prevent Application B too.
Again thanks for your attention:)

Okay, I think maybe AppArmor might do just what you're wanting.  You can define a profile for applications allowing, disallowing certain actions.  It's in the repos and there will be a bit of reading!  I've got it running on my machine but it's been awhile since I set it up.  Check it out.

Barrie

---

### Post by ario on 2009-12-02
Thanks. It looks like that AppArmor was first created with Novel Company. The Company of suse linux. Also SELinux is working like apparmor but more more complex. I will go for AppArmor by now.

---

