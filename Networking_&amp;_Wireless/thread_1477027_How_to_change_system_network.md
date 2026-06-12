---
title: "How to change system network"
date: 2010-05-08
forum: Networking &amp; Wireless
---

### Post by Zaki ur Rehman on 2010-05-08
Hi Guys
I bring my office pc to my home. In office we have a network that we can access only via proxy. At home I have a broadband connection. I didnt find how can I change proxy settings of my default network connection Auto eth0. I made a new connection and I can access to internet by browsing etc (I cant make my new connection "system connection" as the option is disable). But it cant applying on upgrade/update. When I try to update, it says check your internet connection. Please help.

---

### Post by Zorael on 2010-05-08
I'm not sure I understand.

The system connection checkbox is always greyed out, and I'm not sure why. So don't worry about that.

There is a Proxy section in System Settings -> Network Settings. Is that what you're looking for? Could you have a proxy set up there that worked while your computer was at the office, and is only in the way now? (See attached screenshot.)

---

### Post by Zaki ur Rehman on 2010-05-09
Thanx Zorael
I did this and it works for surfing the net. But system cant use it, and update manager is not connecting the net. So I cant upgrade.

---

### Post by Zorael on 2010-05-09
I'm not sure if it helps, but try making the same setting in System Settings when opened as root. Perhaps the update manager listens to root's settings rather than the user's?

Hit Alt+F2 and run '**kdesudo systemsettings**'.

---

