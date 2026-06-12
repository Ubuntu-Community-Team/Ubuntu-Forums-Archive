---
title: "Wireless Network Problem"
date: 2011-02-21
forum: Networking &amp; Wireless
---

### Post by tom1252 on 2011-02-21
Hi,

After all the trouble of downloading error riddled copy's of the latest ubuntu OS, i have yet again come up with more troubles. All though it has been a challenged I think it is cracking piece of software, and it's FREE. Anyway I have a WG111v2 Netgear dongle. I have followed the following guide [10 steps of how to set up WiFi (Netgear WG111) on Ubuntu - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=202254&highlight=wg111+netgear"), the best i can. It is for the older version and a few things have changed. (E.g. Buttons have different names.). Anyway it has picked up a neighbours wireless network but can't find mine. So i tried to add it manually and that worked and says it is connected but no Internet connection. Any idea's why? 

Thanks

Tom

P.S The router is the same one as i am connected to wired.

---

### Post by tom1252 on 2011-02-21
Could it be to do with security? I.e wep key

---

### Post by grahammechanical on 2011-02-21
If it can find your neighbor's wireless network then wireless is working fine. What do you mean, it cannot find your network? Is it not in the list of available networks? Or do you mean network manager fails to connect when you try to connect?

Regards.

---

### Post by thefasterblueone on 2011-02-21
Your network should work "out of the box" according to this document.

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear#USB]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear#USB")

The guide you followed is dated 2006, Ubuntu 10.10 is well equipped to handle your Realtek 8187 chipset.

---

### Post by tom1252 on 2011-02-22
Yeah it's not on the available list. I have to create it but it doesn't seem to connect to the Internet. It just connects to the router. Thanks for the replys

---

### Post by tom1252 on 2011-02-22
Anyone have any idea's? I would be very greatful.

---

### Post by grahammechanical on 2011-02-22
As of this moment on my machine network manager is detecting five available wireless networks in range, including my own. Network manager scans and put in the list information about networks that it gets from the modems in range that are broadcasting that information.

You say your network is not on the list. Your modem is not working or you are not in range or the modem is not connecting to the ISP.

Regards.

---

### Post by HouTex on 2011-02-23
> **grahammechanical said:**
> As of this moment on my machine network manager is detecting five available wireless networks in range, including my own. Network manager scans and put in the list information about networks that it gets from the modems in range that are broadcasting that information.
 
You say your network is not on the list. Your modem is not working or you are not in range or the modem is not connecting to the ISP.
 
Regards.
 
I have the same problem as the OP's.  I have two WAPs in my home.  One is an old Linksys (a WAP54G) and the other is a new D-Link 1522 that I operate in AP mode.  I have never been able to "see" the D-Link in either Wicd or Network Manager (even though it's on and working--my Blue Ray DVD connects with it just fine and my Windows Vista laptop connects as well) while I can see and connect to the Linksys WAP.  And it's clearly in range--I've placed my laptop just a few feet away from the WAP and still does not see it.  I've tried disabling all encryption but I still can't see the D-Link in Wicd or Network Manager even though I see other WAPs (i.e. my neighbors and my Linksys WAPs).  My guess is that there is some setting in the D-Link setup program that is causing this.  Luckily for me, unlike some other WAPs, the 1522 has wired connections I can use when I want to work in that room.  But at least in my case it's not a case of the modem not working, or not being in range or that the modem is not connecting to the ISP.

---

### Post by tom1252 on 2011-02-23
Hi, 

I have juts moved my computer and put it with in about a few feet of the router but it can't find it. Yet the same model router that my neighbour has can be picked up. This is strange!

---

### Post by HouTex on 2011-02-23
> **tom1252 said:**
> Hi, 
 
I have juts moved my computer and put it with in about a few feet of the router but it can't find it. Yet the same model router that my neighbour has can be picked up. This is strange!
 
I'm a newbie, but my guess is that it is a setting in your wireless router's setup program that is causing the problem.  I think that is why I can connect to one of my WAPs but not the other.

---

### Post by tom1252 on 2011-02-23
Thanks HouTex. 

Anyone have any experience in trying to sort this problem. I can log in to the router to changed the settings, but not sure what to change.

---

### Post by HouTex on 2011-02-23
> **tom1252 said:**
> Thanks HouTex. 
 
Anyone have any experience in trying to sort this problem. I can log in to the router to changed the settings, but not sure what to change.
 
I just found the thread below.  Apparently, some wireless cards have problems running Ubuntu with a 5 GHz WAP/router speed.  My D-Link 1522 is duel speed and I have been using the higher 5 GHz speed as recommended by the DVD maker.  I have the option to set it to the slower 2.4 GHz.  I'll try that and see if it helps, but keeping Netflix working on my Blue Ray player has a higher priority for me.
 
[http://ubuntuforums.org/showthread.php?t=1462953&highlight=5+ghz](http://ubuntuforums.org/showthread.php?t=1462953&highlight=5+ghz)

---

### Post by tom1252 on 2011-02-23
Thanks so much i am having a look now.

---

### Post by tom1252 on 2011-02-23
This is the router i have:

[http://www.ebuyer.com/product/78906](http://www.ebuyer.com/product/78906)

---

### Post by tom1252 on 2011-02-23
I have gone through some of the router settings. I have changed the  security type from WEP, WPA and none at all. No luck. I have no idea  what to do. Windows is so much easier to setup wireless network but  Ubuntu is a lot better at other stuff, otherwise i would have gone back.

---

### Post by tom1252 on 2011-02-24
Also when I try and manually connect to my router, it asks for the key and I type it in. A message pops up says wireless disconnected and then asks for the key again. Forgot to mention that.

---

### Post by eltomate on 2011-02-28
My WG111 (not sure what version) works better with the drivers I got via the linux-firmware-nonfree package ('apt-get install linux-firmware-nonfree' on the command line) than it did under ndiswrapper.  You might try that.

I might be able to help further if that fails, if you don't mind mashing stuff out on the command line.

---

### Post by KegHead on 2011-02-28
Hi!

Just a FYI--about 4-5 days ago I did an upgrade and lost my wifi connections. A few days later I upgraded again and my wifi works perfectly.

If you have access to a land line try an upgrade via terminal.


KegHead

---

### Post by eltomate on 2011-02-28
> **HouTex said:**
> [...]Apparently, some wireless cards have problems running Ubuntu with a 5 GHz WAP/router speed.  My D-Link 1522 is duel speed and I have been using the higher 5 GHz speed as recommended by the DVD maker.  I have the option to set it to the slower 2.4 GHz. [...]

  I'm assuming by "5Gz" you mean 802.11a, and "2.4GHz" means 802.11b/g.  The gotcha with the 5GHz frequency is shorter range, so your best bet would be a pure 802.11g (no b) network.  If you enable a mixed g/b network, you'll lose a good chunk of speed.  Some routers have an option to disable 802.11b, very good idea unless you have b-only devices.

  Point being, your Netflix will run the same or better on 802.11g (2.4GHz), assuming you don't have a lot of interference on that spectrum.  FYI, most/all microwaves operate on that frequency, so pop your popcorn before the movie unless you like stuttering. :)

---

