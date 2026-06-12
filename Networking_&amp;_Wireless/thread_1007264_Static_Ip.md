---
title: "Static Ip"
date: 2008-12-10
forum: Networking &amp; Wireless
---

### Post by Oliver.BS on 2008-12-10
I am really getting annoyed I want to set up a home network but I now dont want to use SSH or VNC etc Is this possible by the following:

Buy a Domain 
Register a Static IP
Set the Static IP to my Router 
Connect my Dell Laptop Running Linux to the router via Ethernet 

Then would I be able to type in the ip address into the web browser and connect to my network and drag any file off my Laptop ? 

From work ? 

Is this an easier way than using VNC or SSH

---

### Post by Zack McCool on 2008-12-10
There are better ways, using ssh...

Buying a domain is rather cheap, but getting a static IP may not be.  And opening the file sharing ports directly to the internet is rather dangerous.

Here's a better way...   Use your existing broadband connection.  Register a DNS name with ZoneEdit.com.  Depending on your router, you may be able to set up auto IP updating right from your router's config, or you may need to install an app into your system to do the updates.

Install SSH on your home machine.

On your work machine, install WinSCP.  This will allow you to connect to yourdomain.com, and have a Windows-Explorer type interface to drag and drop files from home to work, and vice-versa.

Even if you do go to the added expense of a static IP, you still will want to use SSH for security.  It just isn't wise to open Samba or NFS directly to the internet, unless your files don't mean anything to you...

---

### Post by hyper_ch on 2008-12-10
or use no-ip.com (client in the repos: noip2) or dyndns.org (also client in the repos)

---

### Post by rolnics on 2008-12-10
Why not do use the mac address of each item in the network to specify an ip or should i say reserve that ip? my netgear router does this for me.

---

### Post by Oliver.BS on 2008-12-10
is their a guide to this I am just about to pull my hair out oh and the client is going to be a mac.

---

### Post by rolnics on 2008-12-10
> **Oliver.BS said:**
> is their a guide to this?

Do you mean a guide to my reply or someone elses?? 

If it is my reply you are meaning, then let us know the make and model of your router?

---

### Post by superprash2003 on 2008-12-10
no ip is a good option.. please mention which way you want to go about doing it..

---

