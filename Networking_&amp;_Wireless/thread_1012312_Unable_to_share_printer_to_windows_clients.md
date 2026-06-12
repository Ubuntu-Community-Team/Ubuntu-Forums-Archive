---
title: "Unable to share printer to windows clients"
date: 2008-12-15
forum: Networking &amp; Wireless
---

### Post by oopere on 2008-12-15
I have recently installed ubuntu on a machine. I have successfully added an HP deskjet 3845 printer which works correctly when printing from the local machine. I have shared the printer via cups. From other windows clients I can manage the printers (pdf, the 3845) and have installed the printer without any problems. However, when printing I get the pages printed flipped horizontally and centered vertically. (btw, I was able to install a different printer and use it successfully from windows)

As a workaround I have tried to share the printer via samba, which I had already set up for file sharing, adding 

printcap name=cups
printing=cups
load printers=yes

to the [global] section and
path=/var/spool/samba
guest ok=yes
printable=yes

to the [printers] section

Now the printers appear to the windows machines. I am able to install the printer, however when double clicking on the printer i get the message "access denied, unable to connect" in the window title bar. A test page prints ok but when I try to print from any application, selecting this printer causes the whole setting up of print options a veeeeery slooooow procedure, i.e. completelly useless. 

So, I have two questions:
1. Why do I get flipped and centered printouts using cups?
2. What have I forgotten when setting up samba that causes this slow behaviour?

Pere

---

### Post by HuntMike79 on 2009-02-13
Did you find a solution to this in the end?

I'm getting the exact same problem... "access denied, unable to connect"

---

