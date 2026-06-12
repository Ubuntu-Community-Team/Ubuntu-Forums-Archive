---
title: "Networking problems after upgrading to Kubuntu 9.04"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by Ederico on 2009-04-24
Just when I have no time to waste, I upgrade from Kubuntu 8.10 to Kubuntu 9.04 to have the best available Kubuntu (supposedly). I'm becoming ever more reluctant to do upgrades as I always experience some nicety. If it ain't broken, don't fix it. Upgrading should be about improvement and greater ease of use, not this. 

Anyways, to the problem! My previous network settings have apparently been removed, the network management aplpet that used to appear in the taskbar is not there and I can't seem to manage to connect trough wi-fi using Network Settings under System Settings.

Wired ethernet works, but I need wi-fi.

Can anyone please help? Thanks beforehand.

---

### Post by weyrick on 2009-04-24
> **Ederico said:**
> Just when I have no time to waste, I upgrade from Kubuntu 8.10 to Kubuntu 9.04 to have the best available Kubuntu (supposedly). I'm becoming ever more reluctant to do upgrades as I always experience some nicety. If it ain't broken, don't fix it. Upgrading should be about improvement and greater ease of use, not this. 

Anyways, to the problem! My previous network settings have apparently been removed, the network management aplpet that used to appear in the taskbar is not there and I can't seem to manage to connect trough wi-fi using Network Settings under System Settings.

Wired ethernet works, but I need wi-fi.

Can anyone please help? Thanks beforehand.

I can confirm this exact same problem, also looking for solution...

---

### Post by Ederico on 2009-04-24
I admit utmost stupidity, I managed to discover that there is a plasma widget rather than the previous applet. Problem solved, sorry for the previous tone, terrible exam stress occasionally leads to terrible manners!

Good job to the developers, this looks better!

---

### Post by CohenTheBarbarian on 2009-04-25
If there is  WORKING plasma widget, please  describe how to use it (post screenshot if avilable). 

I have the same problem. Knetworkmanager worked just fine. Now, after update I don't have wireless (and I dont have cable network - I have to use windows to post this message). Network is configured in Network Management (kubuntu see my network, as other networks in vincinity) but it doesn't connect. I found plasma widget "network management" but only thing it does is showing me stats of network usage (flat line on zero, of course).

Is there a way to reinstall knetwork manager?? It worked perfectly for me and I want my wireless back. Without it i can simply delete kubuntu and return to windows, because without internet my laptop is useless :(

---

### Post by Ederico on 2009-04-25
My Kubuntu is in Italian, so I doubt any screenshot would help.

You just have to install the widget in the manner you install all other widgets on the desktop. It worked for me that way, didn't need to change any settings.

Sorry if I can't be much of help, but I'm no expert myself.

However, in this link there is something about the widget itself - [http://www.kubuntu.org/news/9.04-release](http://www.kubuntu.org/news/9.04-release)

---

### Post by abn91c on 2009-04-25
+1, had same issue and I saw a bug report somewhere that adding the networking widget to the taskbar again, then doing the normal wireless set up there works I did that on my inspiron with Broadcom 4318 and it worked.

---

### Post by CohenTheBarbarian on 2009-04-26
I resolved the problem by re-installing kubuntu. I downloaded jaunty from kubuntu.org and installed it on my old system. It worked (well, partially, my desktop effect messed up), applet appeared like it should. After that I made a backup of home folder and I made a clean install of jaunty on formated partition. This solved all of my problems. 

I can only assume, that error (showing network monitor instead of network management) occurs when you upgrade from 8.10.  Now I will think twice before the upgrade :(

---

### Post by jetpeach on 2009-04-26
EDIT I was typing the wrong password because I had forgotten the correct one. Now with the regular plasmoid one my WPA2 connection is working fine.



I just did a clean install on my Dell Inspiron 1420n (original came with Ubuntu 6.06 preinstalled) and can't connect to wifi (WPA2). It just keeps asking for the password, which I know I'm typing correctly.

This is using the default network manager plasma program. I read and it seems this is a problem with this new KDE4 network manager, and I could not find a good workaround. Please if anybody knows a workaround, I guess I'll fiddle around trying to use the gnome-network manager for now.

Any help is appreciated!
jetpeach

---

### Post by dastasha on 2009-04-30
So can I confirm that mobile wireless mobile broadband worked with a fresh install of Jaunty? The upgrade path was a fail for me. I´ve tried deleting the plasmoid, tried wicd (couldnt configure with my modem), deleted and reinstalled knetwork manager several times.

Kubuntu 8.10 recognised my wireless broadband usb modem (e220) at install.
If I download the iso and do a fresh install, will Jaunty do the same?

Perhaps - I would prefer - to persevere with knetwork which I have reinstalled, after deleting the plasmoid network manager.
It looks and appears the same as it was under intrepid - however the checkbox next to the ISP I have configured is missing. I´ve deleted then re-added the settings for the ISP.
I can switch to another users login - when I attempt to connect, I get the purple rotating gear icon - blue (connected) light on the modem. Then the connection is dropped.
There is no action at all under the primary logon.

I would prefer not to do a fresh install. Others appear to have made the upgrade path work -

---

### Post by nadrach on 2009-05-06
Fresh install of Kubuntu 9.04 after virus destroyed last remaining windows machine. However, we have a wireless router (code-locked to ISP) which requires an ASCII WEP key. KDE3 on 8.04 allowed "passphrase", "hex" and "ascii" option, KDE4 on 9.04 only allows "passphrase" and "hex". Why drop the "ascii" option? I cannot risk upgrading other machines from 8.04 without an "ascii" option in the WiFi setup. Any suggestions?

---

### Post by nadrach on 2009-05-06
Further ... have tried translating WEP ASCII key to hex, but after saving setup, when I reopen the WiFi setup, it always returns to "passphrase" setting, does not appear to save a hex key as a hex key (and it still will not connect)

... also, I now have options for "DHCP" and "Auto IP" to assign an IP number ... what is the difference, and which should I use with a BT 2091 modem/router

Oh, and now I have mucked around with it, the "auto-connect" function has stopped, and now the widget will not even try to connect. How do I force a WiFi connection attempt?

---

