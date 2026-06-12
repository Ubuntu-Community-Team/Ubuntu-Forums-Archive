---
title: "Applet Networkmanager : how does it work or ... does it work with WEP ?"
date: 2009-07-04
forum: Networking &amp; Wireless
---

### Post by Spear on 2009-07-04
Hi there !

Being an " old school " linux guy, i recently realized once i installed Ubuntu Netbook Remix, that there's nothing left in /etc/network/interfaces :confused:

I killed the Networkmanager thing and came back to the old interfaces file to have things work okay.

I wanted to try Sidux, and as it wasn't more satisfying for me than ubuntu is ont the netbook, i reinstalled the latest Netbook Remix version. Of course, i could break the networkmanager thing again, but it could be useful to have it once wandering and getting hotspots, but i can't manager to make it work.

Here's what's going on :

It detects the wifi. I click on it, then, first thing :

1) It only purposes WPA & WPA 2 personal.

Does it mean that WEP 128 isn't managed by the default connection mode ?

2) Even if i paste the key, it doesn't work, but another interesting thing is, that if i paste the key, and it tries to connect, when the window comes back, if i " unhide " the key, it's not the same anymore i pasted a few secs ago.

3) If i try to create a new WIFI Network by hand, then being able to choose WEP 128 and static IP ... yes, i can do it, but i don't seem to find a way to " connect " to that network, if i click on a detected network, it comes back to that " WPA & WPA 2 personal window ". Is there a way to use the configurations manually configured for a detected network ?

4) Where does Networkmanager store it's conf files ? There's nothing interesting in /etc/networkmanager.

Honestly, i'm fed up, is there any solution, or any existing tool that makes you easily connect to a detected Hotspot wethere it is on WEP, or WPA ?

Thanks in advance to the community !

Have a good day !

---

### Post by spd106 on 2009-07-04
Hello,


1) Network Manager tries to be helpful and show you the encryption type it has detected the AP (Access Point or Router) uses. This isn't 100% reliable, but it's usually correct. Check that your AP doesn't have the ssid broadcast turned off. The workaround is to use the Connect to Hidden Wireless Network... where you can specify the settings. This option is available on 9.04, though I'm not sure if it is on UNR yet.

2) The WPA key is transformed with the ESSID into a 64-bit hex representation as per the WPA spec. It's this that you see when you reveal the key. This probably a user interface bug, but it works regardless.

3) Creating a new network is really for Ad-hoc networks and using the PC as a replacement AP. It's not used for connecting to an AP.

4) The settings are stored in gconf and keyrings, there aren't any central .conf files as such. Network Manager will not interfere with any interfaces defined in the /etc/network/interfaces file, so you can still do it the old way if you want to. See *man interfaces*.

Hope this helps.

---

### Post by Spear on 2010-01-15
Hi,

With the latest version, i have the same problem.

The workaround with the " invisible network " from spd106 works (a late " thank you " by the way :)), but isn't satisfying.

I finally found out a definitive solution : wicd package. works perfectly out of the box, haven't had any problems since i installed it.

I removed the boring Network manager on all the laptops and replaced it by wicd.

---

