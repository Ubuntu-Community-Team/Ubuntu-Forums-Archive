---
title: "Brother MFC-665CW Printer And Ubuntu 9.10"
date: 2010-04-17
forum: Networking &amp; Wireless
---

### Post by belkinsa on 2010-04-17
Before you post this link going back to the main topic: [http://ubuntuforums.org/showthread.php?t=301112](http://ubuntuforums.org/showthread.php?t=301112), I have read the topic and done what marwl said to do.  Installed the drivers, but when I tried the last part, I still don't get a printed test page.  This is on Ubuntu 9.10.  Any ideas?

---

### Post by pdc on 2010-04-18
so you went here

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-665CW](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-665CW)

and downloaded the lpr and cupswrapper drivers as .deb versions

and followed the pre-install instructions from here

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#002](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#002)

and created a symbolic link as they recommend

> sudo ln -s /etc/init.d/cups /etc/init.d/lpd

or if you have 64bit

>     Ubuntu 64 bit version
    
    **_Requirement_**
    ia32-libs or lib32stdc++ is required to be installed.

and then followed all the Brother instructions on this page

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html)

---

### Post by belkinsa on 2010-04-18
I forgot the code below. Thanks.

But when I do a test page the CUPS 1.4.1 "Prite Jobs" pages gives me this:

>    completed at
Sun 18 Apr 2010 09:13:21 AM EDT 
*"Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect"*

and I don't get a printed test page.

---

### Post by belkinsa on 2010-08-29
First of all, sorry for the bump.  Second of all, I have an update.  Finally, I got it working under 10.04.  I think a factory reset on the printer helped.

---

