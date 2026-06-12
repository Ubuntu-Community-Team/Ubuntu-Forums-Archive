---
title: "Wireless: No autoconnect after 9.04 upgrade"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by GuiGuy on 2009-04-26
It's hard to remain cheerful after the 9.04 upgrade. I've just managed to alienate my wife after upgrading her computer. 

The wireless network connection no longer connects automatically after login, despite  "Automatically Connect" being checked in the network manager. 

Have to connect manually by opening the KDE system configuration applet, then networking, blah blah blah.

Very tedious....

Any help. (Keep it simple please, my head is really starting to hurt) ;)

Cheers

---

### Post by GuiGuy on 2009-04-26
nevermind. A purge and re-install of the KDE plasma applet fixed it.

---

### Post by JMakowski on 2009-04-27
OK.  Forgive a newbie, but how do you do this in Kubuntu?

I upgraded to 9.04 and remember having Internet after upgrade.  But now it's not connected.

Also, I am using a DLink Wireless card and the madwifi driver.  I don't think the wireless shows under System Settings/Networking.  And not sure I see a Network Manager anywhere on my system even though I didn't really fool with the Install any when it was freshly installed.  Seems like some things on my Kubuntu system just are not there.

---

### Post by GuiGuy on 2009-04-28
> **JMakowski said:**
> 
Also, I am using a DLink Wireless card and the madwifi driver.  I don't think the wireless shows under System Settings/Networking.  And not sure I see a Network Manager anywhere on my system even though I didn't really fool with the Install any when it was freshly installed.  Seems like some things on my Kubuntu system just are not there.

1)Open synaptic

2) Check network-manager is installed. If not, mark it for installation.

3) Find plasma-widget-network-manager

4) If it is installed, mark it for re-installation. If not installed, mark it for installation.

5) Install


You should now have the network plasmoid in the panel. Click on it to see if your network interface is present. 

Let us now if this starts to work for you.

---

### Post by Takis on 2009-05-04
+1, thanks!

---

