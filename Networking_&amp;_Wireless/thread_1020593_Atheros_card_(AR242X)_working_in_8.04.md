---
title: "Atheros card (AR242X) working in 8.04"
date: 2008-12-24
forum: Networking &amp; Wireless
---

### Post by Sami00Sami on 2008-12-24
My first actual post here, so: Thank you thousand times for every excellent post that have helped solve my linux problems. My first 3 years as Linux novice have passed and I think that its my time to give little contribution back to the community. 

This is short description how I got my sisters wireless card working after trying several different possible solutions.

The laptop is **Acer Travelmate 4315** with _Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)_.

You can check your pci-based Ethernet adapter by

```
lspci | grep Ethernet
```

The restricted-drivers-manager didn't work at all so I list all the different try-outs that I made: 

[LIST]
[*][COLOR="Red"]**MadWifi-project  (invalid solution)**[/COLOR]

[INDENT][_(homepage)_]("http://madwifi-project.org/wiki/news/20081106/new-primary-project-domain") 

There is great installation script for MadWifi drivers made by Kajaste [_(link here)_]("http://ubuntuforums.org/showthread.php?t=798485"), so I don't bother to tell all the other ways to install Madwifi modules. 
 
I found out that even the latest svn-version of madwifi didn't support this model. I got couple of HAL errors in **dmesg** (13, then 0xf(?) and some other octal error message). Founded out that these bugs were stated as non-fixable. 

[/INDENT]
[*][COLOR="DarkOrange"]**NdisWrapper** (working partially)[/COLOR]

[INDENT]To get this working go to acer support select your model of notebook and download latest XP wireless drivers. Also install "Windows Wireless Drivers" from "add/remove application tool". After installation it can found in System->Admin... Then the installation of windows-driver should be no-brainer.

*[COLOR="DarkRed"]The problem of this I found was that once one while it doesn't connect to networks that have been used before (some voodoo moves will fix this temporarily).[/COLOR]*
[/INDENT]

[*][COLOR="Lime"]**Linux wireless (working)**[/COLOR]

[INDENT][_Follow this link and its instructions._]("http://linuxwireless.org/en/users/Download") When you are at the **LOAD** section, module that you need to load is,

```
sudo modprobe ath5k
```

To make sure this module is loaded at boot time add,

```
ath5k
```

to **/etc/modules** file. 

I guess that these driver-modules are the same what 8.10 uses, because I have heard that in I.I. this type of cards works out-of-box.

[/INDENT]
[/LIST]

I hope this helps somebody out there. I can't guarantee that I response to this thread, because lack of time. I have 4 Ubuntus to maintain plus 3 computers of my own and I have also my real job (that isn't IT-related).

---

