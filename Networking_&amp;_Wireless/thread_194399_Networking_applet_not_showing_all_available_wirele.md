---
title: "Networking applet not showing all available wireless networks."
date: 2006-06-11
forum: Networking &amp; Wireless
---

### Post by robfindlay on 2006-06-11
I've just done a clean install of Dapper, and the normal gnome networking applet only shows one access point instead of the other one my company is using. 

I boot into windblows and it shows both, then I boot back over to Dapper and it's only got the one again.  

Thing is I need to get into both. 


Niether one is running WEP or WPA etc,  my machine is a DeLL 6000 with a 2200BG card. 

Any ideas?  Is there a better a networking manager then the one that comes with gnome? 

Rob

---

### Post by nikolokolus on 2006-06-11
are you using network manager with nm-applet?

if you aren't sure, just open a terminal and run the following command:

'ps -e' (sans quotes) and look for the two processes.

I've had very good success letting network manager handle my wireless connections.  If you aren't having much success with GUI network scanning there are command line tools (too many to enumerate right now) that will allow you to see what is within range. The wiki here: 
[https://wiki.ubuntu.com/WifiDocs/WirelessTroubleShootingGuide?action=show&redirect=WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WifiDocs/WirelessTroubleShootingGuide?action=show&redirect=WirelessTroubleshootingGuide)

has some great information about troubleshooting your wireless card.

---

### Post by robfindlay on 2006-06-11
[QUOTE=nikolokolus]are you using network manager with nm-applet?

if you aren't sure, just open a terminal and run the following command:

'ps -e' (sans quotes) and look for the two processes.

I've had very good success letting network manager handle my wireless connections.  If you aren't having much success with GUI network scanning there are command line tools (too many to enumerate right now) that will allow you to see what is within range. The wiki here: 
[https://wiki.ubuntu.com/WifiDocs/WirelessTroubleShootingGuide?action=show&redirect=WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WifiDocs/WirelessTroubleShootingGuide?action=show&redirect=WirelessTroubleshootingGuide)

has some great information about troubleshooting your wireless card.[/QUOTE]


I'm running Network Monitor 2.12.0

---

