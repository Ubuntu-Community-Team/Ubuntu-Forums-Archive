---
title: "Network Manager keeps asking for password"
date: 2009-11-11
forum: Networking &amp; Wireless
---

### Post by robth on 2009-11-11
I'm having problems with Ubuntu 9.10 and my wireless connection. I can connect to my wireless network (SSID hidden, WPA2 protected), but it takes anywhere from 30 seconds to half an hour (argh !) to get a connection. The Network Manager detects the network and tries to connect, but it keeps asking me for the password over and over again #-o. When I check the password in the NM it is the correct password. Also in Seahorse, the correct password is stored.

Note that I'm running a fresh install of Ubuntu 9.10, without any tweaks, wireless modifications etc. No config files changed. It is an out of the box install.

I don't understand why NM is asking me for my password. It saved it, right? It makes no sense to ask for the password, since it is in Seahorse. If I wanted to change the password I would have done so in Seahorse or NM itself, since they are linked.

And why does it take so much time to connect?

I hope this problem can be solved soon since I find it very disappointing. I'm a big fan of Ubuntu and it works great except for the wireless connection. But this is of course very important!

Does anyone have any clues?
Thanks,
Rob

---

### Post by maxvaillancourt on 2009-11-11
I have the same problem for the password, in 9.10 as well. Every time I login, (I am set to Auto-Login), Network-Manager keeps asking me for the password I set him the first time I connected to my Wi-Fi network.

---

### Post by mdwyer39 on 2009-11-15
Same thing keeps happening to me. My Network manager sees my wireless network but won't connect to it. It keeps asking me for my password and then finally fails. I followed the steps to the load the windows wireless driver from the _**Help: Wireless Troubleshooting:**_

_5.2.3.&#8195;Using Windows Wireless Drivers_

Ubuntu supports a system known as NDISWrapper. This allows you to use a Windows wireless device driver under Ubuntu.
   1. Obtain the Windows Driver for your system and locate the file that ends with .inf.
   2. Install the ndisgtk package.
   3. Open ndisgtk (System &#9656; Administration &#9656; Windows Wireless Drivers).
   4. Select Install new driver.
   5. Choose the location of your Windows .inf file and click Install.
 _  6. Click OK._

Once I have intalled the .inf file the wireless network driver software shows  "no hardware present" for netnw245. Any ideas on how to fix this? I'm using the D-Link DWA-130.  I have even tired removing Network manager and installing wicd but that was less successful. It didn't even see any wireless networks.

Help please

---

### Post by robth on 2009-11-23
For me the problem was solved by removing the Network Manager and installing Wicd.

---

### Post by AFI420 on 2009-11-23
i prefer wicd, but did you check the box that says something like you connection for all users? i heard that fixed this before

---

### Post by robth on 2009-11-25
I did try, but to no avail. Thanks for your tip though! I'm one happy Wicd customer now :D

---

### Post by j ferguson on 2010-01-16
I went through the same aggravations with 9.10, network-manager and a DWA-130.  I found the stuff about ndiswrapper, used the driver that came with the DWA-130 rev E. fooled around with it for hours and then saw this page. used Synaptics package manager to get WiCD, whose installation took well over an hour on my Compaq M300 PIII 500mHz.  it just ran and ran and ran and ran.  finally a page came up from Wicd claiming to show the networks.  it didn't.

I had to tell it my wireless interface was wlan0.  then it worked and after an hour trying to log on to someone else's Verizon Mi-Fi, I hit the start-over button on my Mi-Fi and it was off to the races.  

Network-Manager could see the wifi sites including my Mi-Fi but couldn't talk to them - odd.

---

