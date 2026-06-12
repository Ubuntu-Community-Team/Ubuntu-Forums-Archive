---
title: "Can't Access Win 7 Shares from Lucid"
date: 2010-08-04
forum: Networking &amp; Wireless
---

### Post by ArcherTC on 2010-08-04
Hello -- I am trying to access a shared printer connected to my Win7 PC from a laptop running Lucid Lynx.  I have Samba installed and configured okay (I think) and I can browse the Ubuntu laptop from Windows but when I try to access shares on the Win7 machine I get a message NT_STATUS_UNSUCCESSFUL.

I've reviewed the security settings on the Win7 machine and tried turning off the firewall.  I can see the Win7 computer on my network and ping it from the Ubuntu laptop but I cannot access shared folders or the printer.

Any help greatly appreciated!

---

### Post by fredbird67 on 2010-08-04
It sounds like you don't have your computer set up to be shared in Windows 7.  I just Googled this and found something similar in which someone wanted to know how to share a printer connected to a Windows 7 box with his Mac.  Hopefully the "On the Windows 7 PC" paragraph of the following will be of help to you:

[http://social.answers.microsoft.com/Forums/en-US/w7performance/thread/bd920e46-dbeb-4bb2-a38e-8791facd0608]("http://social.answers.microsoft.com/Forums/en-US/w7performance/thread/bd920e46-dbeb-4bb2-a38e-8791facd0608")

Hope this helps!
Fred in St. Louis

---

### Post by ArcherTC on 2010-08-06
SOLVED (mostly) -- after more research I learned that this is a known Samba issue.  There is a conflict with the "Windows Live ID Sign-in Assistant".  After deleting that utility from my Windows 7 PC I am able to access the (Windows 7) attached printer from my Ubuntu Laptop, my primary concern.  I still can't browse the network but at least I can print.

---

