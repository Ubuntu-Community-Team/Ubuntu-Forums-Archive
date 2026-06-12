---
title: "how can i connect remotely to windows through RemoteDesktopViewer"
date: 2009-12-09
forum: Networking &amp; Wireless
---

### Post by mady03sam on 2009-12-09
[SIZE=3]hi evrbudy,
                 im unable to resolve dis issue regardin remotely connecting to windows PC through Remote Desktop Viewer from ubuntu im gettin a error msg like Connection to host <remote desktop ip>:5900 was closed. 
        but why dis happenin here i need to connect evry pc in ma network
[/SIZE]

---

### Post by ubhi on 2009-12-09
your window firewall block that port.. either open this port on windows or disable window firewall.

---

### Post by gradinaruvasile on 2009-12-09
> **mady03sam said:**
> [SIZE=3]hi evrbudy,
                 im unable to resolve dis issue regardin remotely connecting to windows PC through Remote Desktop Viewer from ubuntu im gettin a error msg like Connection to host <remote desktop ip>:5900 was closed. 
        but why dis happenin here i need to connect evry pc in ma network
[/SIZE]

Remote Desktop in Ubuntu ITS NOT Remote Desktop in Windows.
Windows uses the RDP protocol, Ubuntu has only a built in VNC server. Totally different technologies.

Use GRDC/Remmina instead. Open a terminal and type:
If you are using Karmic (Ubuntu 9.10):

sudo apt-get install remmina

Ubuntu 9.04 or lower:

sudo apt-get install grdc

Then make sure you select Remote Desktop Connection protocol (RDP - Windows terminal service)

---

