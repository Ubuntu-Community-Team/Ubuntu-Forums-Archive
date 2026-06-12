---
title: "No access on second desktop."
date: 2011-11-10
forum: Multimedia Software
---

### Post by Tuxaby on 2011-11-10
I have a on-board AMD HD4250 and a Asus AMD EAH6850.  I successfully installed Catalyst 11.10 and succeeded in getting both cards recognized and the screens at the correct resolution.  Everything is there except for any access (no top tool-bar, no Unity access and a X for a cursor) on the second screen through HDMI on the 4250.  I get a standard desktop on the primary screen through HDMI on the 6850, complete with all access.  How can I get the desktop cloned on the second screen so I have access there as well?
  [COLOR=#2323dc]MY rig: Asus M4A88TD-V EVO/USB motherboard, AMD Phenom II X4 955 Black Edition , on-board Radeon HD4250/[/COLOR][COLOR=#2323dc]Samsung LN-T4042H TV[/COLOR][COLOR=#2323dc] and  ASUS Radeon EAH6850   PCIE/[/COLOR][COLOR=#2323dc]ASUS VW246H LCD[/COLOR][COLOR=#2323dc], 8GB Kingston HyperX DDR3 1333 SDRAM  RAM,  Antec TruePower New TP-650 650W PSU, COOLER MASTER Centurion 5 case,  and , 2- Western Digital Caviar Black WD1502FAEX 1.5TB hard drives, Logitech MX 5500 Bluetooth mouse and keyboard, Ubuntu 11.10, and Win 7 Pro.[/COLOR]

---

### Post by Tuxaby on 2011-11-11
I solved the problem myself.  I had used this how to[COLOR=Blue][COLOR=Plum]([/COLOR] [http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide)]("http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide")[/COLOR] to set up everything.  I started here after a fresh install of Ubuntu 11.10, [3.2 Installing Catalyst Manually (from AMD/ATI's site)]("http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29").   The only settings I had not done was tried Xinerama, as it would never duplicate the correct resolution on past fresh install tries using other tutorials.   Not seeing any results from this thread I decided to try Xinerama.  The result was just what I had wanted in the first place.  Resolutions were correct and everything was accessible.

---

