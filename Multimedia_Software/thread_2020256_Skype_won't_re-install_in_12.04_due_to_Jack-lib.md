---
title: "Skype won't re-install in 12.04 due to Jack-lib"
date: 2012-07-08
forum: Multimedia Software
---

### Post by Flash Kid on 2012-07-08
Good evening, all.  Well, I really need help on this, but I don't know where to begin.  Starting about yesterday, I had troubles running Skype.  It would cause my computer to freeze, so I thought, "well I'll uninstall and reinstall, maybe a file is corrupted."  However, when I try to reinstall, dpkg fails and gives me this messsage:
```
E: /var/cache/apt/archives/libjack-jackd2-0_1.9.8~dfsg.2-1precise1_i386.deb: './usr/share/doc/libjack-jackd2-0/buildinfo.gz' is different from the same file on the system
```

My machine is 64-bit and I had attempted before to install the Jackd2-0:i386 package a long time ago because certain codecs for playing VCDs weren't working.  However, the package was broken, so I had to completely remove it.  But now, I don't know what on earth to do.  I wish I knew how to give more information, but I don't.  Please help.

Flash Kid

---

### Post by Flash Kid on 2012-07-08
Nevermind for now, I suppose :S  I ran apt-get and installed all of the updates, then reinstalled Skype, and for some reason now, it runs fine!  Sorry for causing a ruckus, I just hate it when I can't figure stuff out. :p

---

