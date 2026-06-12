---
title: "Jaunty network printing issues - workaround"
date: 2009-07-13
forum: Networking &amp; Wireless
---

### Post by timzak on 2009-07-13
I recently upgraded the machine on my home network that has the printer attached from Hardy to Jaunty.  After doing so, I lost the ability to network print via localhost:631.  

If I discover the printer, it works, but because my home network uses DHCP, sometimes the IP address of the printing computer changes, and the network machines can't seem to rediscover the new IP.  So that's not working.

Setting the printer to localhost:631 (rather than a static IP) used to work, but now it cannot find the computer/printer in this configuration.  Reading up on the forums here, it appears to be a common problem with Jaunty, so I'm guessing there's a bug somewhere.

The workaround is to set the network printer to Samba/Windows Shares.  Even though I don't have a Windows machine on my network, I do use Samba for file sharing.  The trick is, the printing setup won't find the printer using Samba/Windows unless you manually navigate to the machine via Samba through Nautilus, enter the username and password, then open the printer ($print folder).  Once this is done, go back to Administration->Printing and set the printer up through Samba/Windows and make sure you have it remember the username and password of the machine with the printer.

Has anyone else had network printing issues with Jaunty?

Hope this can help someone else.

---

### Post by SteveDee on 2009-07-14
I fixed my network printing issues by modifying the smb.conf file in line with the advice from forum member swerdna.

Check the printer info at the bottom of this linked page: [http://ubuntu.swerdna.org/ubulanprimer.html#appendix](http://ubuntu.swerdna.org/ubulanprimer.html#appendix)

---

