---
title: "What's the difference between these drivers?"
date: 2011-03-19
forum: Networking &amp; Wireless
---

### Post by Torp3x on 2011-03-19
I downloaded and installed the drivers from the following source:

[http://www.janoweb.net/drivers-patch/compat-wireless-aircrack-maverick-patched.tar.bz2](http://www.janoweb.net/drivers-patch/compat-wireless-aircrack-maverick-patched.tar.bz2)

Worked fine in aircrack, but unfortunately gave me terrible download speeds, which lead me to post this thread [http://ubuntuforums.org/showthread.php?t=1709630](http://ubuntuforums.org/showthread.php?t=1709630)

I then installed the drivers from this source:

[http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2)

which fixed my download speeds. 


I have an Atheros 9k card and an Alfa AWUS036H. Presumably the janoweb maverick patched drivers are suitable for aircrack, and the unpatched compat-wireless drivers are suitable for internet browsing, but neither driver can be used for both purposes? 

Is there some way to achieve the best of both worlds, without having to install/uninstall different drivers for each device? 

What role does the mac80211 driver play in all of this?

---

### Post by atomicben on 2011-07-15
Jano has a nice tut here:
[http://forum.aircrack-ng.org/index.php?topic=5755.0](http://forum.aircrack-ng.org/index.php?topic=5755.0)

It seems to indicate that:

RTL8187 (which uses the mac80211 stack; whatever that means) is good for your regular internet browsing

r8187 (which uses the ieee stack) is better for aircrack.

I don't get that conclusion because I use RTL8187 for both internet and aircrack.  Now, I should say that I get inject like a HERO with it however, when I try to connect to distant routers my speeds are slow,  BUT, when I connect to mine (just a few feet away) it works fine.

My (totally uneducated noob) conclusion is that the RTL8187 is very sensitive (aka works great) when 'discovering' networks and it can 'burst'/inject very well.  But for some reason that sensitivity gives us the false expectation that we're going to be able to connect and download with the same sort of quality.

I find that for the AP's that are further away, my internal Broadcom (b43 drivers) work better at maintaining connection and throughput (provided I can see it and connect) - even though the signal strength is no where near what the RTL8187 'says' it's getting.

To sum it up, I can inject and capture with the RTL8187 from very far away (I'm amazed at the captures I get at great distances) but after connecting it seems to lose it's range and throughput speeds unless you're sitting on top of the AP.

---

