---
title: "Ubuntu 10.10 64bit wireless problems"
date: 2011-03-19
forum: Networking &amp; Wireless
---

### Post by ncsufan95 on 2011-03-19
I recently installed Ubuntu 10.10 inside Windows 7 Home Premium via wubi. There seems to be some problems with the wireless connection, as i got the "device not ready (firmware missing)" error. I then downloaded some drivers and messed around and that went away, but i still can only get on the internet with eth0.

Right now, when i click on the wireless gnome-panel applet, it says that i am connect to (SSID) but when i actually click on the wireless network under the applet, i get disconnected.

Any suggestions?

Oh yeah, i cant seem to be able to install any of the drivers, or the b43 fwcutter and anything like that, i just get errors in terminal.
thanks.

---

### Post by Sef on 2011-03-19
> Oh yeah, i cant seem to be able to install any of the drivers, or the b43 fwcutter and anything like that, i just get errors in terminal.

What errors do you get? Please copy and paste them here.

---

### Post by ncsufan95 on 2011-03-20
Ok, system>administration>additional drivers. It searches, and comes up with 3
-NVIDIA accelerated graphics driver (not activated)
-Broadcom STA wireless driver (activated)
-NVIDIA accelerated graphics driver (version current) [recommended]
--For some reason, i dont see the B43 driver anymore?

For the terminal command "sudo apt-get install b43-fwcutter", i get: Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 283 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up firmware-b43legacy-installer (4.178.10.4-4) ...
Not supported card here (PCI id 14e4:4315)!
Use b43 firmware. This is just for the b43legacy driver.
Aborting.
dpkg: error processing firmware-b43legacy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43legacy-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

---Oh, i tried to download advanced desktop effect settings (compiz) and it failed, so i looked at the code and one chunk of it read :

Setting up firmware-b43legacy-installer (4.178.10.4-4) ...
Not supported card here (PCI id 14e4:4315)!
Use b43 firmware. This is just for the b43legacy driver.
Aborting.
dpkg: error processing firmware-b43legacy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up python-compizconfig (0.8.4-2ubuntu2) ...
Setting up compizconfig-settings-manager (0.8.2-0ubuntu1) ...
Processing triggers for python-support ...
Processing triggers for python-central ...
Errors were encountered while processing:
 firmware-b43legacy-installer
Setting up firmware-b43legacy-installer (4.178.10.4-4) ...
Not supported card here (PCI id 14e4:4315)!
Use b43 firmware. This is just for the b43legacy driver.
Aborting.
dpkg: error processing firmware-b43legacy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
---i just noticed that it had "firmware-b43legacy-installer", so maybe that can help my problem

---

### Post by chrysdeblogue on 2011-03-24
hello !
same s...!...
anyone plz ?

---

