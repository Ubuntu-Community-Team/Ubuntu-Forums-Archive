---
title: "using WEP"
date: 2009-12-07
forum: Networking &amp; Wireless
---

### Post by phantomhead on 2009-12-07
I was able to login to a wireless network in my hotel using Win XP. I think it uses 801 variant. The modem is Netgear. 

Now when I try to connect to the same wireless network using Ubuntu, I get a WPA message box asking for the password. After this, it tries to connect and asks for the password again. 

How do I get this to work. Is there some kind of incompatibility between the modem and the wireless networking on my computer.

I havent done any setup on the ubuntu side. The WPA message box came up by itself. I tried using other protocols but had no luck

phantom

---

### Post by diablo75 on 2009-12-07
I would start by going to (in Ubuntu) System>Preferences>Network and delete all the wireless networks listed in the Wireless tab (or at least all the ones that match the network name you're trying to connect to).  Once that's cleared out, attempt to connect to the network again.  My only guess behind this is that the password needed to connect to the network was mistyped and then saved.  Either that.... or there's a problem with the drivers for the adapter.

---

### Post by phantomhead on 2009-12-07
I already cleaned out the wireless networks setup, but I am going to do it again to see if makes any difference.

so other than the password thing, I am wondering if there's any difference in how the Router is configured and how Ubuntu is talking to it in wireless mode?

I have never worked with WPA or WPA2 Personal before. I am thinking all I have to do is set the password and it will work right. But that hasn't worked like that so far.

---

### Post by phantomhead on 2009-12-07
How do I setup 802.11 variant on Ubuntu. I tried using the existing wizards but the accept button on the window wasn't highlighting unless I give the password of a certain length. This isn't the case when using Win XP.

---

### Post by lewisforlife on 2009-12-07
I cannot connect to a WEP encrypted network.  I have a friend that has spent a lot of time on the forums trying to figure this out.  From what we can figure out, WEP is not supported by Ubuntu due to a bug.  This bug exists in 9.04 and 9.10.  I can connect to WEP using Windows on my laptop, if I am in Ubuntu on the same laptop I cannot connect to WEP, and I keep getting prompted for a WPA password.

If my information is not correct, and there is not really a bug, please let me and phantomhead how to solve this problem.  But as far as I can tell, it is impossible to connect to WEP from Ubuntu.

---

### Post by dandnsmith on 2009-12-07
I think this must be one of those awkward areas.
I managed to connect using WEP with Ubuntu 8.10 from an Acer Aspire One - it wouldn't cooperate with using WPA.
When I tried Mint (5?), then I could get WPA as a possibility.
Some of the other wireless networking bits were also a bit different.
Possibly the hardware+driver is a bit critical.

The repetition of requests for the login password (not the WPA/WEP password) is my personal bugbear.

---

