---
title: "Cannot send/recieve data on college campus WiFi"
date: 2010-02-08
forum: Networking &amp; Wireless
---

### Post by daminkz on 2010-02-08
I am sorry but this problem has been bugging me for the past 3 weeks.

I came back to school this semester after installing Ubuntu. I have no problem connecting to our school's wireless network. The problem is after connection. When a user tries to browse the web, they are first brought to a gateway, in which the user needs to enter their e-mail to validate themselves. 

In XP, this always worked. In ubuntu, **after redirection**, the connection hangs and eventually times out. This happens every time. I have tried changing IPv6 settings to no avail. 

I have searched google and came to a bug report in which the user had the same problem to me. He said it had to do with MAC filtering, which it seems my college campus is doing after reading the live headers. The bug report was closed, however, so I could not find a suitable solution.

If anyone has any information on whether this is a problem with Ubuntu or a problem with my school's authentication system, please let me know. It is very inconvenient to have to work on my laptop and then transfer files via USB stick to print them at school.

---

### Post by unmole on 2010-02-08
I doubt the issue is MAC filtering because you were able to access the same hotspot with the same machine. (I use Ubuntu to connect to my university's WiFi which implements MAC filtering without any issue).

---

### Post by adam814 on 2010-02-08
If it still works in XP it isn't MAC filtering causing your problem as the same NIC should have the same MAC (unless changed in software) in Linux as it does in Windows.  You could confirm this speaking to the "help desk" and asking if they use MAC filtering.  I doubt they would though, why have an admin adding MAC addresses to the "allowed" list all day long in router configs when it doesn't provide any security at all?

Do you have for example an option to use a VPN connection?  I also attend a university with a similar campus wifi system.  Using the "login page" proceeds to send all your data in the clear over unencrypted wifi.  I find this unacceptable, so I've set up vpnc  to connect to their dedicated VPN servers.  This way all my data gets encrypted.

---

### Post by daminkz on 2010-02-08
I have tried to address the issue to campus IT staff, but have come empty handed. My e-mails go unanswered and I cannot even talk to a real person at the campus.

This issue is very weird indeed. I should try this on a different laptop running Ubuntu, so I can verify that it is not just my computer, or that my MAC address hasn't been banned. (Hard to imagine as we are only allowed to pull traffic through port 80.)

---

