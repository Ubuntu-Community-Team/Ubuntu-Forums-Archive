---
title: "How do I set /proc/fs/cifs/LinuxExtensionsEnabled permanently?"
date: 2009-03-19
forum: Networking &amp; Wireless
---

### Post by akameswaran on 2009-03-19
Ok - the first version of the question is:
How can I set /proc/fs/cifs/LinuxExtensionsEnabled to 0 permanently
I of course can echo it in once a system is running, but that's ugly.

Actually - I suspect I'm troubleshooting the wrong problem, but it would work.

I have a NAS (dns-323) that I just used to replace my old NAS.  smbfs and cifs both seem a little odd on my boxes compared to my old setup, but it works on my wife's linux laptop.

We're both running ubuntu 8.10, but I have the ppc (Ps3) version running, and for some odd reason, I cannot mount using cifs unless I change the parameter /proc/fs/cifs/LinuxExtenstionsEnabled to 0.

Then everything works on the PS3.  It's interesting that I didn't have to do any such thing and my wife's laptop has the setting at 1, and basically works just fine with an entry in fstab.  Now, the new NAS is definitely not happy using nautilus, etc whereas the old one worked.  But if my cifs mount points work I am happy.

Anyway, on the Ps3, using the same settings to the same share, always gave me not a directory error=20 cifs error.  I set the above /proc/fs setting and at least mount -t yada yada works.

But fstab setting doesn't work until i can find a way to permanently set the variable - and as opposed to other things I've played with I can't find a setting in /etc/sysctl.conf or /etc/sysctl.d/*

Personally I think it's odd that it works on the x86 laptop, but not on the ppc PS3 in linux (not even sure if it's worth comparing modules/library versions - both systems are versions 8.10)  But hey I'd rather just get my NAS up and running rather than worry about why I need different configs for the same os to the NAS share.  n

---

