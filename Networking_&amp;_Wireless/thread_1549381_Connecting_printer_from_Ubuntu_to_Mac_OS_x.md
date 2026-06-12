---
title: "Connecting printer from Ubuntu to Mac OS x"
date: 2010-08-09
forum: Networking &amp; Wireless
---

### Post by l0uismustdie on 2010-08-09
Hello.  I am running Mac OS X 10.6.4 and Ubuntu 10.04 on a Dell Dimension 2400 desktop.  I have recently connect a printer to the desktop (which is connected to a Belkin Basic wireless router).  I have since been trying to print from my Macbook Pro through the Dell desktop.  I was able to print from a HP laptop also running Ubuntu 10.04.  

Some things I have tried:
I have set up cups and it is definitely running.  I have been to the admin page and made sure "share printers connected to this system" and "allow printing from the internet" are checked.  I have opened port 631 on my firewall.  I have tried to connected directed to the IP address of my Dell desktop from my mac.  If anyone has any other ideas or if I am missing something please post and let me know.

Thanks

---

### Post by wookieshaver on 2010-08-09
I'v shamelessly stolen this from the Ubuntu Documentation Wiki but here goes as it sounds like you've done some but not all of this:
 
**On the machine sharing the printer - the server**

[LIST=1]
[*]Open the **System -> Administration -> Printing** launcher for [FONT=Consolas]system-config-printer[/FONT] application.
[*]In the "Printer configuration" dialog box, select the **Server -> Settings** menu.
[*]In the "Basic Server Settings" dialog box, select the option **Publish shared printers connected to this system**
[*]Going back to the "Printer configuration" dialog box, open the Properties dialog box for your printer
[*]Open the "Policies" view and make sure that **Enabled**, **Accepting Jobs**, and **Shared** are selected
[/LIST]

---

### Post by l0uismustdie on 2010-08-09
Thanks for your reply but it turns out I have gone through all of those steps already.

Any other ideas out there?

---

### Post by biglebronski on 2011-06-26
Hi. Sorry, I don't have any help for you on this subject, but I was wondering if you might be able to tell me which 10.6.4 distro you got to work on that Dimension 2400.

Thanks in advance,
Dominic

---

