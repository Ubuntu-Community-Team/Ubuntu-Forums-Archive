---
title: "Wireless did work"
date: 2008-12-17
forum: Networking &amp; Wireless
---

### Post by brianiajf1 on 2008-12-17
(noob) When I run the live cd my wireless jsut worked took that forgranted and installed dual boot system ubuntu and xp. When i log in to ubuntu now it doesnt show my wirless networks or that adaptor but i can scan and see the adapter any ideas where to go

---

### Post by einstein on 2008-12-17
Interesting phenomena.  I upgraded a desktop from Hardy to Intrepid over last night.  The computer has a wireless card that never did work (even under windows).  Anyhow, as the upgrade completed, I noticed the Network Manager showing the wireless card fully active - being skeptical, I waited for the signal to reboot but delayed, unplugged the wired card and pinged Google.  It really was working!  On reboot, the computer saw all the wireless networks in the neighbour hood but would not connect.  Second boot, the wireless card was back to dead as usual.

No, iwlist scan says nothing out there.  ifconfig says card exists.

What giffs??!

Does Intrepid networking still use the /etc/network/interfaces file?  Changes in System->Preferences->Network Configuration do not show up there.

Also, the 'puter delays a long time while booting - apparently waiting for the wireless network to come up.  This happens on a Toshiba A200 as well but CTRL+ALT+DEL gets the boot process going again and, once logged in, I can <almost> always get the wireless network up without difficulty.

Intrepid's mobile computing improvements are looking a bit buggy....

---

### Post by Clancy_s on 2008-12-17
*This happens on a Toshiba A200 as well but CTRL+ALT+DEL gets the boot process going again and, once logged in, I can <almost> always get the wireless network up without difficulty.*

How do you get it up?  I have an A200, can't get wireless to work under Intrepid (64 bit).  wicd works fine for wireless but looses my ethernet card...

I'm trying to fix one or the other...

---

### Post by einstein on 2008-12-18
Good question, Clancy.  I don't know.  I uninstalled Network Manager on the A200 (32 bit) and installed Wicd - (as I just did on my desktop about five minutes ago).  Wired networking on the A200 has never been a problem - I think I borrowed the Vista driver from the original OS for the wireless adapter and installed it with Ndiswrapper.

Network Manager is starting to look to me like, well, a mistake.  It has caused mega problems for me in two of three upgrades.  It probably missed on the third one because it is headless server setup.

---

### Post by madsmaddad on 2008-12-18
I have exactly the same problem. Live on a 3COM wireless USB stick, and under 7.1 and previous I had to configure Wpa_supplicant to get it working. Installed from a Live CD on another computer and it picked up wireless, easy to configure encryption, and worked, so I upgraded over the Internet from 7.1 to 8.10. Now no wireless, can't find wireless configuration programs. 

Am writing this after booting into the XP side. 

Hope that someone has some ideas. I am reluctant to delete all the wpa_supplicant stuff until I have something solid to try.

In catch 22 situation - No network, so can't download fixes.

---

### Post by Clancy_s on 2008-12-18
> **einstein said:**
> Network Manager is starting to look to me like, well, a mistake.  It has caused mega problems for me in two of three upgrades.  It probably missed on the third one because it is headless server setup.

Agreed.  Even when it does work I prefer the wicd interface.

I discovered my ethernet card is now eth1 not eth0.  Once I changed that in wicd preferences I can connect to wired with wicd.  It's not perfect - when I do wicd loses my wireless (says no networks found even when it's 20cm from the router) and can't  find it again 'til it's restarted.  I can live with that until after Christmas. :rolleyes:

---

### Post by Ayuthia on 2008-12-18
> **madsmaddad said:**
> I have exactly the same problem. Live on a 3COM wireless USB stick, and under 7.1 and previous I had to configure Wpa_supplicant to get it working. Installed from a Live CD on another computer and it picked up wireless, easy to configure encryption, and worked, so I upgraded over the Internet from 7.1 to 8.10. Now no wireless, can't find wireless configuration programs. 

Am writing this after booting into the XP side. 

Hope that someone has some ideas. I am reluctant to delete all the wpa_supplicant stuff until I have something solid to try.

In catch 22 situation - No network, so can't download fixes.

Is this an upgrade or a fresh install?  If it is an upgrade, have you tried to use the previous kernel?

---

### Post by madsmaddad on 2008-12-19
It was an upgrade. according to lsb_release -a the system is now 8.10 where it was 7.10 before. (to the best of my memory. I am doing this from the dark (XP) side.)

I have the CD, but I didn't want to do a full install from CD, as that would just add another operating system, so I found  the instructions on here somewhere for upgrading across the LAN, and did that. 

MMD

---

### Post by madsmaddad on 2008-12-19
Sorted. Thanks to all you guys. I did a ps -ef|grep wpa and found a number of wpa files. 

I looked through my notes from when I got wpa supplicant working under 7.1, and found that I had created an rc.local file  in /etc that ran at startup and ran all the commands to start the wireless config. I deleted this file and rebooted, and lo, I am writing this from Kubuntu. 

One happy guy. 

mmd.

---

