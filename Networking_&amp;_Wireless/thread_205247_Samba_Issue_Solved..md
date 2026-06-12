---
title: "Samba Issue Solved."
date: 2006-06-28
forum: Networking &amp; Wireless
---

### Post by blaquesmith0 on 2006-06-28
I had the same samba problem of not being able to find or mount my share through normal means. Assuming one followed the samba install guides (as I have). I could only find my LinBox via smb://ip_address in Linux or connect to my ip_addres on WinBox. I couldn't just browse for MSHOME Clients. Long story short. I edited my /etc/hosts.conf where LocalHost is 127.0.0.1 and the error appears to be username-desktop(hostname) being 127.0.1.1. Just change the 127.0.1.1 to 127.0.0.1. Then after a quick sudo /etc/init.d/samba restart. nautilus can now browse MSHOME and find both the WinBox and my LinBox on my network. And the WinBox can know browse and find my LinBox share as well as browse for my now networked PDF_Printer (Cups PDF).] So stop banging your head (*,) with that complex workaround.
-blaquesmith0

---

