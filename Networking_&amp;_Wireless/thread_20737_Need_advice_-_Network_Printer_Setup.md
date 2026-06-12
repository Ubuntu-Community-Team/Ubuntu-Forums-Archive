---
title: "Need advice - Network Printer Setup"
date: 2005-03-18
forum: Networking &amp; Wireless
---

### Post by iminj on 2005-03-18
I have a 3 machine mixed OS network ( Ubuntu / XP / Win98 ). Here's the configuration:

Ubuntu - printer on parallel port
Win98  - printer on parallel port
XP        - no printer attached

The GOOD NEWS .. is that I've already installed and configured SAMBA / SWAT, and all 3 machines can share the 2 printers. Here's my problem:

I just added Ubuntu (now dual boot) to the Win98 box. The printer is locally connected on Parallel port. **How should I configure print sharing on the network when I boot this box into Ubuntu?** When I do this, I have 2 linux boxes with connected printers. **I still want the 3rd machine (XP only) to have access to both printers.**

Should I configure SAMBA on the ubuntu side of the dual boot machine ? Or should I use CUPS ... or some other protocol ? My gut instinct says that I need Samba to keep the XP machine served with printers. Any advice is welcomed ....

thanks -iminj

---

### Post by kleeman on 2005-03-18
Stick with your gut and install SAMBA on the dual boot machine. You might have to create a new printer on the XP machine to deal with the new Ubuntu.

---

### Post by Mr Black on 2005-03-19
I don't know if you want to invest any money or not, but I have delt with a few multi OS environments at home and I've found the best way to handle printing is by directly connecting the printer to the network and then setting up the printers via direct IP (use CUPS under Ubuntu and just create a standard IP port in windows).  You can use [one of these guys](http://www.netgear.com/products/details/PS101.php) , or something like it, to get the printer connected.  This way you won't have to worry about one of the boxes going down for any reason and not having printing on another machine cause its using a shared connection from the downed box.

I suppose you could also use some sort of KVM switch that has print support as well or a router that has the print server built right in it.  Anyway hope this helps.

---

### Post by iminj on 2005-03-19
Mr. Black:

Thanks for the advice about using Print Servers; and I agree that adding them to my network would simplify things (esp. having printer access without worrying whether or not a PC is offline). 

I'm not ready to cough up $200-$250 for 2 wireless/parallel print servers (yet) ... so I'm going to stick with my current configuration and try to get it working.

As I mentioned in my 1st post, in my Ubuntu/XP/Win98 network ... Samba works well. However, when I dual boot my Win98 box into Ubuntu (in effect, now having 2 Ubuntu and 1 XP box) printer sharing fails. I installed Samba on the 2nd Ubuntu box .... but for some reason, the Ubuntu machines can't share each others printer.

**Question: Is there any reason that you can't have more than 1 Samba Server on a network at the same time ?**

-iminj

---

