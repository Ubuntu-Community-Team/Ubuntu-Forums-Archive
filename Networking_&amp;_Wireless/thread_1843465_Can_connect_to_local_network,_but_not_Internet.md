---
title: "Can connect to local network, but not Internet"
date: 2011-09-13
forum: Networking &amp; Wireless
---

### Post by ox45tallboy on 2011-09-13
Greetings. I use Ubuntu for the TimeTrex server at an office I do IT work for. (If you're not familiar with TimeTrex, it's a timecard program with a web-based interface so the users can clock in and out from their desktops.) Recently, I was notified that Timetrex was giving incorrect clock in/out times. Upon investigation, I found that the server had the incorrect time due to drift from it being close to 8 years old. For some reason, the built-in Ubuntu clock adjuster was not adjusting the time. 

It took a while, but I figured out that it wasn't adjusting the time because it had no Internet access. It was still able to see the network (users get to TimeTrex through an icon with its IP and port on their Windows desktops, we don't have a local WINS server or other name resolution) but not the Internet. At first I thought it was a DNS issue, but I can't ping 8.8.8.8 or any other Internet IP, although I can ping internal addresses. 

My network setup is a Juniper SSG-5 Firewall performing DHCP for all the workstations @ .100-.199, with the Ubuntu server hardcoded to .201 .

When I first installed it, I had Internet access on the box (I performed the updates), and I think one of the managers decided to "fix" it one day. What should I be checking for?

Thank you in advance.

---

### Post by ox45tallboy on 2011-09-13
If there is other information I can post that will help, please let me know.

---

### Post by ox45tallboy on 2011-09-13
Okay, finally got it. In /etc/network/interfaces, I forgot to include the line 

auto eth0

Edited this file, restarted networking, and I'm good to go. Now the manager is complaining that the clock outs are going to show ~30 minutes off. Sheesh, you can't please some people.

---

