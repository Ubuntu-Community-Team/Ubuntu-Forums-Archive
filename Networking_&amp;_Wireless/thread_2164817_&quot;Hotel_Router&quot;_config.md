---
title: "&quot;Hotel Router&quot; config"
date: 2013-08-02
forum: Networking &amp; Wireless
---

### Post by hathalud on 2013-08-02
Hey folks!

My girlfriend just moved into a motel for an extended period of time and they only provide wireless internet access to one device for the room at a time. Considering that there are at least 5 devices in the room that function best with an wifi internet connection I want to set her up with a homebrew ubuntu router. This allows the "router" to be accessed and the sign-on motel authentication to be performed, since it's not just a matter of putting in a password for the right wifi network. Additionally, there is no wired network connection in the room. Ergo a router-to-router store bought solution is not the solution here. 

We have an older HP Mini (netbook with a Broadcom wifi adapter) with an Atheros usb wifi adapter for a second wifi. I've installed Ubuntu 12.4 and everything is cool. Added the madwifi drivers and the network stops working. And since this is my 3rd pass at this from the ground up, I'm breaking this down into phases. lol. (I'm even doing backups after each stage)

Right now I have the router-netbook with just Ubuntu 12.4 installed and the madwifi drivers are installed, but the calls in the /etc/network/interfaces for the madwifi settings are commented out, else the netbook does not get on the network at all. 

So, where do we start troubleshooting this? Uncommenting those lines and restarting the network is easy enough... but what do we do next to gather diagnostic data?

And the next stage after solving this issue is to setup netmasq and create either a bridge from one wifi to the other with a structured network on the second wifi since Android and IOS does not like ad-hoc networks (and we're not jailbreaking the iPad).

---

### Post by kurt18947 on 2013-08-02
Do the multiple devices need to be wireless?  If not, you could use a wireless bridge.  I did this for grins with an old but still available Linksys WRT-54G and DD-WRT.  I used these directions:

[How To Turn An Old Router Into A Wireless Bridge]("http://www.makeuseof.com/tag/how-to-turn-an-old-router-into-a-wireless-bridge/")

I have no idea how to make everything wireless though I'm sure it can be done.

I sorta thought MadWiFi has been deprecated, not sure though.

---

### Post by hathalud on 2013-08-02
Nearly all the devices are wireless and have no ethernet ports. Tablets and the like are funny like that... such limited space on them for hardware. ;) And the tablets are used more heavily than the other devices.

---

### Post by kurt18947 on 2013-08-02
Only thing I can come up with is a wireless access point plugged into a wireless bridge.  The Rube Goldberg index is pretty high on that idea though:lol:.

---

### Post by hathalud on 2013-08-02
I appreciate the suggestion there, but that's not the option I'd like to follow. For the moment I'd just like someone to help me get the madwifi drivers working or setup some kind of wifi to wifi bridging within Ubuntu. I'm sure that there's someone out with far more Linux know how than me that can assist with this. Or at the very least someone can help me get the madwifi drivers just working. :)

---

