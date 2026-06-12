---
title: "Terminal Server Client How-To"
date: 2005-12-21
forum: Networking &amp; Wireless
---

### Post by rsankuratri on 2005-12-21
I am trying to connect to a windowsXP workstation from my laptop which is running Ubuntu 5.10.  I have tried the following options in the Terminal Server Client Window:
  On the General Tab:
    Computer: raptor (name of the Windows XP machine)
    Protocol: RDP
    UserName: <windowsXP admin user>
    Password:  <windows xp user password>
    Domain: <Blank, as it is not part of a domain>
    Client hostname: mithril (name of the laptop)
    Protocol File:  <Blank>

Rest everything is default on the other tabs.  When I hit connect, it says "Unable to Resolve Host".  If I use the IP address instead of the computer name, it just times out after a couple of minutes.

Can anyone suggest what I have to do or if I am doing anything wrong?

Thanks

Raj

---

### Post by waster on 2005-12-23
can you ping the target machine? what does /etc/resolv.conf say? does internet browsing work? are you behind a firewall?

---

### Post by djgenesis on 2005-12-23
And moreover... Why are you trying to connect through the the RA? This service should be turned off cause it has many vulnerabilities. Try [this]("www.realvnc.com") or [this]("www.tightvnc.com"). 
If you still want to use RA, it would be a good start to provide the info **waster** requested. 
Genxx

---

