---
title: "Ubuntu can't see a list of Windows shared folders"
date: 2009-01-06
forum: Networking &amp; Wireless
---

### Post by adamitj on 2009-01-06
I'm very familiarised with Ubuntu and samba, but I never used ubuntu desktop as a main (and by now, the "only") desktop workstation, so I'm having a problem that I couldn't find nothing about it on this forum.

As I said, my ubuntu desktop running Intrepid Ibex (8.10) is now my only workstation. The company uses a new server running Microsoft Windows 2003 Server, with a lot of shared folders. The server's name is "SERVIDOR" and is accessed by internal ip 192.168.100.250.

I'm trying to show a list of shared folders (as when typed \\192.168.100.250 at MS Windows), but Ubuntu can't see the list of folders.

All other workstations running Windows can see the list.

Is there some bad setup on Windows Server or into my ubuntu instalation?

[COLOR="DarkRed"]**P.S.: If I try to connect directly into a shared folder by its name there is no problem at all (i.e.: smb://192.168.100.250/desenv).**[/COLOR]

---

### Post by superprash2003 on 2009-01-06
whathappens when you open  smb://192.168.100.250 under places->network

---

### Post by adamitj on 2009-01-06
I used places->network and tryied to access "SERVIDOR" (instead of ip address, the network list shows the server name).

No matter how I try with smb://servidor or smb://192.168.100.250, the shared folders does not appears.

---

### Post by Tomdarkness on 2009-01-06
Excally the same problem here. When I try and view a list of shares/printers on a Windows server (Windows Server 2003 Enterprise Edition) it does not display anything. Although like you said, if I manually type in the share or printer name it connects fine.

---

