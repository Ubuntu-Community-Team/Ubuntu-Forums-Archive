---
title: "Goodbye Ubuntu (for now)"
date: 2009-02-28
forum: Networking &amp; Wireless
---

### Post by joey-elijah on 2009-02-28
I've recently moved rooms which means i can only connect to the internet via wifi. The access point is literally down a long hall. 

Ubuntu just fails with my USB wifi dongle. It used to work fine but since i've moved rooms it won't. Network manager happily picks up the network and it has a excellent signal, but it just will not connect to it whilst i have WPA. 

I switched the WPA off and it connected fine and had a healthy 82% conenction. Windows 7 gets slightly better reception at 90%~ but i wasn't noticing any slow downs.

The network manager icon just spins and spins when trying to connect/authenticate. I've checked, changed and checked again the WPA password and it's correct but it just won't connect. 

I hope there is something really simple i'm missing as i really love using Ubuntu and have been using it as my main OS for almost a year and a half. It's been a week without it now and arrrgh!! Who would have thought you could MISS an os?!

I try connecting everyday just in case, but i've literally wasted hours waiting for it to... well.. do nothing.

:(

---

### Post by kimberlite on 2009-02-28
Hi joey-elijah,

I think the title of your post is a little bit misleading. As I understood you need help on wifi connection rather than saying good bye to Ubuntu. Why don't you just ask assistance for setting up your dongle? In this case try to give more details, like the output of lsusb command, or the description of the way you used iwconfig, etc. Best wishes...

---

### Post by inigomontoya on 2009-02-28
> The network manager icon just spins and spins when trying to connect/authenticate. I've checked, changed and checked again the WPA password and it's correct but it just won't connect. 

I hope there is something really simple i'm missing as i really love using Ubuntu and have been using it as my main OS for almost a year and a half. It's been a week without it now and arrrgh!! Who would have thought you could MISS an os?!

I try connecting everyday just in case, but i've literally wasted hours waiting for it to... well.. do nothing.



Remove network manager and install wicd.  [http://wicd.sourceforge.net](http://wicd.sourceforge.net)

---

### Post by joey-elijah on 2009-02-28
> **kimberlite said:**
> Why don't you just ask assistance for setting up your dongle? In this case try to give more details, like the output of lsusb command, or the description of the way you used iwconfig, etc. Best wishes...

I have already made about a gazillion threads but no-one seems to help. I've also followed about 10 different tutorials, spent a total of 5 hours in the terminal... I'm literally exhausted by it.

The other problem is i can't log into Ubuntu and post the outputs on here as i'll have no internet connection. Irony! 

> **inigomontoya said:**
> Remove network manager and install wicd.  [http://wicd.sourceforge.net](http://wicd.sourceforge.net)

This was my last resort, and still no luck. It can see the network and tries to connect but the progress bar just keeps loading during 'Authenticating' and then fails. The password is correct as i even changed the password again via my router and wrote it down. I do like WICD as an interface though! The only problem i have now is i cannot reinstall network-manager >_< !

---

### Post by mjoolnir on 2009-02-28
It sounds like the dongle is not powerful enough to transmit to the AP. Try making one of these [http://www.usbwifi.orconhosting.net.nz/](http://www.usbwifi.orconhosting.net.nz/) and pointing it at the AP.

---

### Post by kimberlite on 2009-02-28
And could you tell us please what type of dongle are you using? Cheers.

---

### Post by joey-elijah on 2009-03-01
The dongle must be powerful enough if it can connect fine in Windows and can connect fine without any encryption. It's signal strength (according to network-manager and wcid is 82%) 

It's an SMC WUSBS-N2 and worked fine before. I use x64 bit Ubuntu with the x64bit XP Driver for the dongle via NDISWRAPPER. It normally works fine.

lsub gives the device as: (this is transcribed, not copy n' pasted)
Bus 002 Device 005: ID 083a:b522 Accton Technology Corp. EZ Connect N Draft 11n Wireless USB2.0 Adpater.

So it's showing up, and as i keep saying works fine - just not with WPA.
Anooyingly, i did manage to get online ONCE via network-manager using WPA from this room, but it dropped the connection after 25 mins.

Having uninstalled network-manager to install WCID, i'm stuck using WCID.

---

### Post by woosey on 2009-03-01
If you want a permanent solution, i would look into buying an old linksys WAP/WRT and sticking DD-WRT on it, you could then repeat the original APs signal giving you a much greater range.

---

### Post by joey-elijah on 2009-03-02
I just want to say thanks for all the responses.

I did manage to get reception with my original dongle by switching from WPA/2 to just WPA however the connection would drop every so often and because it was via ndiswrapped i couldn't just 'unplug-plug' to reset the adpater therefore forcing a restart.

BUT! :D

My brother gave me another USB Dongle and this one works 'out-of-the-box' with Ubuntu so i no longer have to forsake security for connection! I'm so stoked!

---

