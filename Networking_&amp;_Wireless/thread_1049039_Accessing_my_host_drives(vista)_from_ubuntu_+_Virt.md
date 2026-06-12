---
title: "Accessing my host drives(vista) from ubuntu + Virtualbox"
date: 2009-01-24
forum: Networking &amp; Wireless
---

### Post by Naif.1 on 2009-01-24
Hi guys,

I am new to ubuntu and I just installed it on virtual box, hosting is Windows Vista.
I am wondering how can I access my C and D drives from ubuntu so that I can use my files..

BTW, I have googled this problem but I couldn't find an answer or solution!

Thanks guys..

---

### Post by Naif.1 on 2009-01-24
up

---

### Post by Noo on 2009-01-27
Try sharing your files in Vista and then go to "network" in "places" in Ubuntu to see the files shared by Vista. Here I assume both Vista and Ubuntu share the same network.

---

### Post by Another Monkey on 2009-01-27
I use Ubuntu 8.10 in VirtualBox 2.1.0 on a Windows XPsp3 host.

First thing, have you checked out the VirtualBox forums to see if your answer is in there?  I recall seeing lots of questions about Vista.

Second, how do you want to access the drives?  Via networking or via VB shared folders?

If via VB shared folders, you **must **install GuestAdditions.  Have you done this?  If so, then the VB docs are very good at explaining what to do.

If via networking, then I think you need to be running the guest with HIF networking.  You will also need Samba Client installed (and Samba if you want to create network share folders on the Ubuntu guest).
You may also need to fix your iptables configuration (either via the "Firestarter" GUI, or by directly hacking the files).
Also, make sure that your Windows networking is set-up correctly and this will depend greatly on what firewall you use on Windows.  The default Windows firewall **will block** file sharing.  In third party firewalls you may need to "trust LAN" or do other stuff - check your documentation.
Easiest way to solve this is to disconnect your router/modem from the internet and then temporarily disable all firewalls.
Test networking, get it going and then bring the firewalls back up one at a time.  If sharing suddenly stops, you know that last firewall is causing a problem.

HTH.

---

