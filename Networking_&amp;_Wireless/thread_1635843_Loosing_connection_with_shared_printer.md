---
title: "Loosing connection with shared printer"
date: 2010-12-02
forum: Networking &amp; Wireless
---

### Post by williepabon on 2010-12-02
I have a home Wi-Fi network with Windows 7  pcs and  a Linux box.  All  machines connect to the Internet via a Linksys router. In the Linux box, I  have configured a printer to be shared by the rest of the network.  Everything works OK for a while. After some idle time, the windows  machines loose connection with the shared printer on the Linux box.  Right now, I solve the problem by resetting the Wi-Fi device on the  Linux box. It should be said that the connection to the Internet is  never lost from any of the  machines (including the Linux box), only the  windows pcs loose connection to the printer. Appreciate your help for a  permanent solution. Thanks.

---

### Post by williepabon on 2010-12-24
Problem is solved! I applied the  solution of a Windows 2000 user that had a similar problem connecting to  a Linux box. He found out that Windows 2K won't connect to a Linux box  if it was identified by its IP address directly. Instead he added a line  on the windows host file (c:\winnt\system32\drivers\etc\hosts) to map the IP address with the Linux box hostname. For example:
#Example hosts entry
192.168.1.101        LinuxBoxName
 I applied the same modification to the Windows 7 host file (same  location) and then ran the Add printer Wizard again: Add printer |  Choose network printer | Stop the scan | Choose printer isn't listed.  The next dialog offers an option to select a shared printer by name. In  the text box, enter the URL of your CUPS based printer, but this time  using the mapped hostname, e.g.,
 [http://linuxboxname:631/printers/printername](http://linuxboxname:631/printers/printername)
 Then, you will get a dialog allowing you to select a windows driver for the printer. That does the trick!

---

### Post by Dark_Stang on 2010-12-24
Nice catch. In the future, I would highly recommend network printers. They make problems like this non existant. ;)

---

