---
title: "Can't connect to unsecured wireless ubuntu 10.04"
date: 2010-09-11
forum: Networking &amp; Wireless
---

### Post by lsquared25 on 2010-09-11
Hey guys, 
so I can connect to any wireless network it seems other than the unsecured wireless network here at my college. As long as you register your mac address, which I did, connection should be fine. I have no issues connecting via ethernet, but I need the wireless also. 

The wireless controller is Intel Wireless WiFi Link 5300. I tried alternatives to the Network Manager and I've looked all over google which I haven't seen many issues, it should work fine.. not sure where to go from here. 

Thanks

---

### Post by lsquared25 on 2010-09-12
bump

---

### Post by specialcowboy on 2010-09-13
I'm having a similar problem on a netbook running 10.04 UNE.  The 5300 card initially connects to my WiFi and then drops the connection and won't reconnect.  I've seen one post on launchpad that suggests this may be a bug with the current kernel?????

Anyone have a solution for this? It's pretty annoying when your WiFi doesn't work.

---

### Post by MaindotC on 2010-09-13
> **lsquared25 said:**
> Hey guys, 
so I can connect to any wireless network it seems other than the unsecured wireless network here at my college.

It's difficult to identify this as a Ubuntu problem seeing as how you can connect to other wireless networks with ease.  You need to seek help from your college's IT staff.  There are things they can verify such as if the mac registration is reaching their 802.1x or RADIUS server and issuing you an ip address in response.  Do you mind if I ask which college?

> **specialcowboy said:**
> I'm having a similar problem on a netbook running 10.04 UNE.  The 5300 card initially connects to my WiFi and then drops the connection and won't reconnect.  I've seen one post on launchpad that suggests this may be a bug with the current kernel?????

This is a separate issue since you can connect.  One post on launchpad doesn't warrant a smear campaign against the current kernel.  Please start a separate thread and consult the [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) and let us know if you have any difficulty and precisely where so we can better help you.

---

### Post by lsquared25 on 2010-09-13
Well I am actually connecting and dropping or I won't connect at all, it's all very intermittent. Just realized if I delete the connection in network manager and then retry connecting to the wireless it works great.

So I'm not sure exactly why taht works, but I'll be stopping by my tech staff. I go to UW Stout in Wisconsin.

---

### Post by MaindotC on 2010-09-13
Ah yes - I forgot about this.  In fact I helped a user [with the same issue](http://georgia.ubuntuforums.org/showthread.php?p=9834634) and his connection worked after deleting the profile.  Sorry I didn't mention it sooner.

There are just some settings that are saved in that profile and for whatever reason those settings were initially configured improperly or corrupted.  Let us know if the problem repeats.

---

