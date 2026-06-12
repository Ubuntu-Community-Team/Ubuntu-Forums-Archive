---
title: "VNC does not work correctly"
date: 2009-10-21
forum: Networking &amp; Wireless
---

### Post by beren on 2009-10-21
Hi,

I have spent quite a bit of time getting to the bottom of this problem - but I need help.aan see thiss work 

I have one laptop and two desktops - all three run Ubuntu 9.04. The two desktops have vino insstalled, the laptop has vinagre installed. Because of the problems I run vnc while I sit next two the screens of the desktops - so I can see what I do remotely on the local screen.

If I setup a vnc connection to desktop one, everything works fine. If I setup a vnc connection to desktop two, I can log in and I see the screen. But when I select a drop down menu, I can see the drop down menu on the local screen - but not through the vnc connection. When I start firefox, I can see the program on the local screen, but not through the vnc connection.

I have tried different combinations of vnc server and viewer - and all have the same issue.

Any suggestions?

---

### Post by beren on 2009-10-24
Hi,

I just tried vnc with Ubuntu from the Live DVD installed on the second desktop PC - and that worked fine. So it must be a firewall / settings issue in my opinion. Suggestions are still very welcome.

Beren

---

### Post by uncle-c on 2009-10-24
VNC usually opens ports between 5900-5903 but that depends onto which port you configure the VNC server when you install . YOU can usually find this by running the netstat -atn command. Hence you can configure your firewall to allow access to this VNC port in order to connect to your VNC server.

---

### Post by beren on 2009-10-25
Thanks for the help - and I got it to work. I reconfigured the firewall, although I am still not sure what the problem was.

One final change needs to be made: After using 'wakeonlan' I want to log in to my desktop without having to login locally.

How do I do that?

Beren

---

