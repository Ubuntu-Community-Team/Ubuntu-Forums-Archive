---
title: "Can't get online with local home router"
date: 2009-07-09
forum: Networking &amp; Wireless
---

### Post by MrCode on 2009-07-09
Helo, all.  I have installed Ubuntu 9.04 recently (as an alternate OS next to Windows XP).  My only way of getting online is though a USB wireless network adapter, and it works just fine in windows.  I've gotten it to work in Ubuntu as well by using ndiswrapper, but I can't seem to connect to my home network router!  What's even stranger, is that it *will* connect to what seems to be a neighbor's router instead.  My home router is WPA2 encrypted.  When I enter the password and hit connect, it will seem to be connecting for a minute or two, and then it'll just say &quot;Wireless network Disconnected. You are now offline.&quot;  I go back into the settings for the network (interface?) and look at the password field, and it appears to have changed to a bunch of hexcodes.  Could that be the problem?  Or is that just my WPA2 pass in ASCII hexcodes?  If neither is the case, is there anything I can do?  I would really rather not use the neighbor's wifi w/o consent...

---

### Post by superprash2003 on 2009-07-10
did you choose the right authentication type like 128bit,64 bit etc? you would have choices , try all of them if your not sure.. if it still doesnt work , try and see if WEP works

---

### Post by MrCode on 2009-07-10
Well, all I could see was a choice between security types (WEP, WPA/2, LEAP, etc.); I couldn't see anything for encryption type...maybe I'm just not looking hard enough.

Also, there's now another problem.  Out of frustration from trying to fix it, I accidentally removed the NetworkManager icon from the top GNOME panel! :oops:  Is there any way I can get it back?  I've tried just about everything I can think of from the command line (that I know won't screw over my system), but nothing brings it back.  There's nothing in the GUI options either.  EDIT: nvr mind about the GNOME icon not being there, it's back after rebooting.

---

### Post by Ed934 on 2009-07-10
> **MrCode said:**
> Well, all I could see was a choice between security types (WEP, WPA/2, LEAP, etc.); I couldn't see anything for encryption type...maybe I'm just not looking hard enough.

Also, there's now another problem.  Out of frustration from trying to fix it, I accidentally removed the NetworkManager icon from the top GNOME panel! :oops:  Is there any way I can get it back?  I've tried just about everything I can think of from the command line (that I know won't screw over my system), but nothing brings it back.  There's nothing in the GUI options either.  EDIT: nvr mind about the GNOME panel not being there, it's back after rebooting.


I deleted NetworkManager once trying to get a wireless card to work on a different computer with Ubuntu. I have to entirely reinstall to get it back! Hope there's away for you, but I eventually just gave up and took the long route....

Ed

---

### Post by MrCode on 2009-07-11
Okay, since I'm pretty well getting tired of this, I figure I should just re-iterate what I'm doing in minute detail:  The Network Manager detects 3 networks in range...we'll call them networks A, B, and C. Network A is the one I'm trying to connect to.  When I boot up the machine into Ubuntu, it attempts to connect to network A (indicating it is doing so by showing the connecting throbber icon in the top panel), and after about 30 seconds it boots me off saying either "Wireless Network Disconnected. You are now offline", or "[Network **B**] Disconnected.  You are now offline."  Network B is unsecured, Network A has WPA2 encryption (and it's the home router, so I know it's password).  Why is it trying to connect to Network B when I want to connect to network A?  Is it because it's unsecured?  Also, Network B comes up first in the list when I open the menu to show the list of wireless networks, whereas Network A appears second.  Network C appears last, but it has an SSID that I don't recognize, and it appears to be secured (there is a small antenna-and-shield icon next to it, like Network A).  The one that is most in range is apparently Network C according to the Network Manager, while Network A is the next nearest, with Network B being the furthest away.  I find it strange that it's trying to connect to the network that's farthest away (and is succeeding).  Should I try connecting to Network C?  Maybe it's some (garbled) alternate SSID for the router I'm trying to connect to?

---

### Post by MrCode on 2009-07-11
Sorry for the bump, but it's the only way I can keep this thread alive (continuous edits wouldn't be noticed, except by maybe a few passing viewers looking for a similar thread)...

I've done some fiddling in the CLI using [this]("http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html") guide, and now I can't get online at all!  it'll still connect to the router (on network B, that is), but I can't get internet access through it.  Have I screwed up things so much that I'll have to re-install Ubuntu?  Or is there still some hope?

I tried every command under the WPA2 list, all to no avail.  I'm pretty sure I have the driver (w/ndiswrapper) correctly installed, but every time I use the wpa_supplicant tool, it reports the wlan0 interface as being disconnected.

plz don't ignore me just cuz I'm somewhat of a CLI noob...I'm really trying, but I just don't know precisely what to do.

---

### Post by steveneddy on 2009-07-11
> **MrCode said:**
>  I accidentally removed the NetworkManager icon from the top GNOME panel! :oops:  Is there any way I can get it back?

I answered that one here:

[http://ubuntuforums.org/showpost.php?p=7601546&postcount=3](http://ubuntuforums.org/showpost.php?p=7601546&postcount=3)

---

### Post by rxbristol on 2009-07-12
I had the same problem today when I was converting a friend's computer from Windows to 8.04 LTS.  The only way I could get the wireless card to connect was to manually set the connection.  After opening the manual setup, I entered the name of the router and set DCHP to auto--it connects every time.  In auto roam mode it would recognize all the routers in the neighborhood and only connect if I forced it.  I would force the connection by making a manual setup and then go back to roam--the only problem with that was I would get a good connection to the router, but it would not connect to the Internet.

---

### Post by MrCode on 2009-07-12
Ok, that's good to know, but that problem has been solved so far...  As for my post above, I've booted back into Ubuntu and I can get online again, but still only with this unknown router...  I apologise for the confusion, but this whole thing seems to be rather shaky.

EDIT:  I see someone has posted before me...  for the "problem sovled so far", I'm referring to steveneddy's post.

---

### Post by MrCode on 2009-07-12
Well, the problem seems to be solved so far...  It apparently was a matter of changing the security type on the router...  It was on WPA2 only at first, but now it's on what's called WPA/WPA2, which I guess may be a sort of WPA-compatible WPA2.

I guess I'll find out if it's permanent next time I reboot.

Thanks for the help, everyone!

EDIT:  It appears to drop out every once in a while...  However resetting the network interfaces seems to work to get the connection back up and running...some of the time.

---

### Post by MrCode on 2009-07-13
Ok, now it's refusing to connect again...  Network B is out of the picture, but it's still attempting to connect (to Network A), and then dropping out before a full connection is established.  I've emailed Netgear about the problem, and I'm still awaiting a reply, but I have a suspicion that they'll just say that I need to use Windows.

I've looked at the log, and I copied and pasted the relevant output to a [file]("http://paste.ubuntu.com/217160/"), in case anyone could maybe take a look at that and see if they can diagnose the problem...  I've looked at it myself (as in I didn't just blindly cut and paste, :wink:), and I'd hazard a guess that my DHCP configs are screwed up somehow?  I don't know what to do about it if that is the problem, but I guess that's where you guys will (hopefully) come in.

---

### Post by MrCode on 2009-07-14
bump plz help?  I even tried using wicd instead of NetworkManager, and it's getting stuck at "Obtaining IP address" when I attempt to connect.

---

### Post by Denver411 on 2009-07-14
Most companies have a great support number you can call... I had a problem resetting my wireless router up and called the company and they kindly walked me through the process again

---

