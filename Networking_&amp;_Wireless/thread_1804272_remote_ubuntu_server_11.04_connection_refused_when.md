---
title: "remote ubuntu server 11.04 connection refused when monitor not connected"
date: 2011-07-14
forum: Networking &amp; Wireless
---

### Post by mohanrajleo on 2011-07-14
hi i done desktop config in ubuntu server 11.04 and connected via tightvnc,uvnc and in remote desktop viewer  from another ubuntu machine also. I am not able to access(connect) the server in GUI mode(when monitor is removed) but i putty is working fine in cmd line.

Any possible way to a access these machine in GUI mode ?...

---

### Post by varelov on 2011-07-14
So basically you have mixed network of ubuntu and win machines that you want to remote via Remote Desktop?
Of course, you have to configure your Ubuntu for that by going to System > Preferences > Remote Desktop and uncheck a box that says "You must confirm each access to this machine". Basically, you have the GUI access to Ubuntu, it's only that you'll have to click "Allow" on its dialog box on Ubuntu machine every time you try to access it remotely. By unchecking the said box you are no longer required clicking "Allow" and your request will go straight through. If of course all you get from Ubuntu when clicking "Connect" is a dark screen. If it's a message like "Coonection closed/refused", then it's more serious problem.
TightVNC has its own bunch of issues, check a topic that I started few topics below yours.

---

