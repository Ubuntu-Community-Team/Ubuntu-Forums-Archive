---
title: "Printing to Win7 shared printer"
date: 2010-09-05
forum: Networking &amp; Wireless
---

### Post by phantom27 on 2010-09-05
I apologize if I'm a little wordy.  I'll give the problem, then a detailed list of my setup (to help troubleshoot).

Problem:  I can't print from Ubuntu 10.4 on my Win7 shared printer.  I also can't connect to the Win7 computer sharing the printer (probably a related problem).  

Error Message: 

1.)  I click on Places, Network, Windows Network.  I get an error that says "Unable to mount location, Failed to retrieve share list from server."

2.)  I click on System, Administration, Printing, Add, Printer, Network Printer, Windows Printer via SAMBA, Browse..., and I get this error "No Print Shares, There were no print shares found.  Please check that the Samba service is marked as trusted in your firewall configuration.  To do this select System->Administration->Firewall from the main menu."

Network Configuration:

I have a wireless/wired network (using a router) where the Ubuntu machine connects wirelessly and the Win7 machine connects wired.  The Win7 machine is on a Win7 homegroup and custom named "workgroup".  There is a username/password to log into the Win7 Machine.

My other Win7 laptop connects just fine to the Win7 desktop's shared printer (and network drives).  I know it isn't a issue of it not working (at least with other Win7 machines)

Problem:

I'm assuming there is probably a setting in Win7 that needs adjusting (although I've looked at about everything I can find).  I also don't know much about Ubuntu so it could very well be something I need to setup in Ubuntu.  I checked already to make sure that SAMBA and the smbfs plugin is installed.

Please Help.

---

### Post by phantom27 on 2010-09-11
I'm still having problems with this if anyone can help I would appreciate it.

---

### Post by MaindotC on 2010-09-11
Is the printer connected to an access point or is it connected to your winblows machine?  If so I suggest you see if your access point has support for uPnP, enable it if you do, and then just plug your printer into the AP and connect to it by ip address.

This doesn't really address the problem you're facing, but it should be a decent work around to allow printing until you can troubleshoot your winblows machine more thoroughtly.

---

### Post by phantom27 on 2010-09-18
First:  I love the term "Winblows"  I've never heard that before!

My Router doesn't have a USB Port but I'm looking at buying the Netgear WNDR37AV and it has a USB Port.  I was planning on using that port for a network drive but maybe a USB hub would work with the router?

---

### Post by MaindotC on 2010-09-18
A usb "hub" really isn't anything that would help with the original issue.  Just plug the printer's network cable into the access point and see if you have uPnP enabled.

---

