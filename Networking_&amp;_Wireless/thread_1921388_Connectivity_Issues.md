---
title: "Connectivity Issues"
date: 2012-02-06
forum: Networking &amp; Wireless
---

### Post by kwchristensen on 2012-02-06
I have the strangest issue that I cannot for the life of me solve. I have 4 computers: a FreeNAS Server, Ubuntu (11.10) Linux Box, a Windows 7 computer and a Windows XP Laptop. Windows MOST of the time will not connect to Ubuntu (Win7 nor XP). I cannot ping it, I cannot ssh and I cannot connect via VNC. It will not connect on the local network or remotely with the proper ports forwarded on the router. However, I can always ping and ssh from FreeNAS into the Linux box without issue - every time. 

The odd part is that once I ping or ssh into Ubuntu from the server Windows will connect to Ubuntu - everything works; SSH and VNC access works flawlessly. It only works for a short period though. Once I disconnect the link is gone and I can no longer connect from windows. Its like a ping from a Linux OS "wakes up" Ubuntu for 5-10 minutes but a ping from windows will not. I checked Ubuntu's ufw firewall, but it is disabled.

To the best of my knowledge I do not recall making any config changes to Ubuntu - the box is not used that often. All remote access worked fine when it was newly installed but one of the updates seems to have broken the connectivity. Does anyone have any idea what would cause this?

---

