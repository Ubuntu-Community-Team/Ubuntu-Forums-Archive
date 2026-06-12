---
title: "No wifi networks showing up on ubuntu"
date: 2011-02-27
forum: Networking &amp; Wireless
---

### Post by jfb112697 on 2011-02-27
Hi my friend just got a dell inspirion 15r (i think), and it comes w/ win7 :( (I HATE Win7) so i made him let me dual-boot with ubuntu maverick meerkat. (he wouldn't let me get rid of win7 cuz thats what his parents use.) It installed successfully, so we booted into it, and there was no wifi networks. I thought it was because wifi was disabled so i press the button i think its F5 but still nothing. I thought it might have been the comp but i booted into win7 (Que the Beethoven's fifth)... and it worked in win7 (thats a first) can someone help me. Oh and i forgot i used that terminal command to unblock wifi

---

### Post by gsgleason on 2011-02-27
Hook it up to a wired network, update the installation, and then check under system -> administration -> additional drivers

That worked for my for a friend's laptop that required proprietary firmware for her wlan card.

Oh, and check the stiky about wireless cards here.  To see what it is, run lspci from command line.

---

### Post by yusof125 on 2011-02-27
Let learn together:

Go to panel bar above and left click at NetworkManager Applet (The notification area applet for managing your network device and connections)

Choose Edit Connections...
Go to Tab Wireless and click Add button

 Connection name: Wireless connection 1
 [/] Connect automatically
 Tab wireless
 wireless SSID: (your preferred WiFi source)
 mode: Infrastructure
 
 Tab wireless security
 security:  (depend to your preferred WiFi source)

 Tab IPv4 Setting
 Method: Automatic (DHCP)

 Tab IPv6 Setting
 Method: Ignore

 [/] Available to all users

 Click apply button then close.

Go to network icon, left single click:
 Choose Wireless Network
 Choose Currently SSID
 Connect to it.

Wait for it working for while.
It's done when it connected.

Do Not Forget To turn ON your WIFI at your notebook!.
Refer to your notebook manual to do that.

by yusof125

---

