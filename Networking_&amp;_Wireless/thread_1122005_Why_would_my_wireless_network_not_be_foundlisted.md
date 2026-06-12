---
title: "Why would my wireless network not be found/listed?"
date: 2009-04-10
forum: Networking &amp; Wireless
---

### Post by YMS_1975 on 2009-04-10
Hi there,

I've posted about something ***related*** to this in another thread ([http://ubuntuforums.org/showthread.php?t=1114729](http://ubuntuforums.org/showthread.php?t=1114729)), however the problem has now somewhat evolved (or failing that, has a new spin to it).

Prior to this post, my network card was not being recognized. After a lot of tweaking and fixing, I now have the card being recognized BUT...now I am unable to connect to my network.

I've turned off the "Disable SSID Broadcast" feature, so theoretically I should see my network name, which I don't. Previously, I had it set up as a hidden network (so this feature was checked).

I had troubles connecting to the network when it was hidden, so I made sure that the network name would be broadcast, however it's still not showing up in my networks list. I can however, see a neighbours (secured) wireless network.

I've rebooted Ubuntu (ver 8.10) but still nothing. I then double-checked the configuration of my router and sure enough it's set to broadcast the network name (SSID), so how come I'm not seeing my network?

Also...when it was hidden, I'd enter in the correct WPA key/PSK and it would just cycle attempting to authenticate, but it would fail. I'm guessing the fact that the network is not showing up on my list is directly related to it not accepting the CORRECT network credentials.

Anybody???

---

### Post by YMS_1975 on 2009-04-10
This is really weird....  :confused:

I disabled all of my network security, then was able to somehow log on to the network (GREAT!). Then I re-enabled all the WPA security on my network.

I've shut down and reboot Ubuntu a few times, and each time I was able to re-connect with the network, but it is NOT asking me for my WPA key, nor does it seem to check the credentials, yet when I go into my router it shows that the WPA security is active.

So it begs the question : **Is my network really secure?**

Under Network Configuration on the Wireless tab, it has network listed as Auto[**My Network Name**]. I remember selecting "Connect Automatically" (when I disabled all the network security), but now when I check the security settings it says NONE. There's no WPA, no WEP, nothing listed at all. I'm afraid of whether or not I'll be able to log onto the network tomorrow. 

"strange days indeed".   :guitar:

---

### Post by Kulgan on 2009-04-10
Try listing the networks with 
```
iwlist scanning
```

Under the interface name you should get more specific details as to what Ubuntu is actually seeing.

---

### Post by YMS_1975 on 2009-04-14
Kulgan...it's ok now. I finally got it to work. Let's just hope it sticks now.   :)

---

