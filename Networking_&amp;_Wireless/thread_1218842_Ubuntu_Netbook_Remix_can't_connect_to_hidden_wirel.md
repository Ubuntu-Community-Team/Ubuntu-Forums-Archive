---
title: "Ubuntu Netbook Remix can't connect to hidden wireless network"
date: 2009-07-21
forum: Networking &amp; Wireless
---

### Post by zrandyc on 2009-07-21
I just installed UNR on an EeePC 1000 that came with WinXP. The wireless worked perfectly with Windows. I cannot connect to my home wireless network with UNR. The router is set not to broadcast the SSID, and it's obvious that UNR can't see it, even when I set a static IP address. UNR does see 6 networks that broadcast their SSID's  from nearby homes. Suggestions?

---

### Post by lns on 2009-07-21
Did you try clicking on the wireless/network manager panel applet and selecting "Connect to hidden wireless network" and filling out the appropriate fields? Do you have MAC filtering turned on in your AP?

---

### Post by zrandyc on 2009-07-21
Yes, I made what seemed to be the correct selections in the Network Mgr, including checking the "connect automatically" box, entering the SSID of the hidden network along with the password, and trying both dhcp and manual IP addressing. I did notice that the password was displayed as hex after one connection attempt. OS X and XP don't do that. No MAC filtering on the AP.

---

### Post by lns on 2009-07-21
Hmm. As a troubleshooting step, why not turn on SSID broadcast temporarily.. what kind of encryption are you using? (not that it should matter, Jaunty can pretty much do it all) 

Since it can see other APs in the area, we at least know your driver is working OK..although some posters here seem to think that the 2.6.30 kernel might be a better bet for wireless performance on the 1000:

[http://forum.eeeuser.com/viewtopic.php?id=67511](http://forum.eeeuser.com/viewtopic.php?id=67511)

kernel 2.6.30 Ubuntu HOWTO:

[http://www.ramoonus.nl/2009/06/10/linux-kernel-2-6-30-installation-guide-for-ubuntu-and-debian-linux/](http://www.ramoonus.nl/2009/06/10/linux-kernel-2-6-30-installation-guide-for-ubuntu-and-debian-linux/)

Keep us updated!

---

### Post by zrandyc on 2009-07-24
It's looking like WPA is the problem. The forums are full of complaints. I will look for a native linux driver  for the Ralink 2860 interface and try that before going through the trouble of switching the kernel.

Editorial comment: WinXP kicks Ubuntu's butt in this area. It's got to get easier if the linux community expects wider adoption of the platform.

P.S. 9.04 includes the ralink drivers. I updated the kernel, but that had no effect. Jaunty clearly is not handling the WPA, as the request for the passkey pops up again and again, but the field is filled in correctly.

---

### Post by lns on 2009-07-24
Hmm, according to [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/339891](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/339891) (looks like the master bug for this issue), if WPA *is* the issue (did you try temporarily turning WPA off?), you can simply enable jaunty-backports, update the system and reboot (this will give you the latest RALINK 2860 drivers which fix the bug supposedly).

Go to System -> Administration -> Software Sources and click on the "Updates" tab. Select "Unsupported updates (jaunty-backports)" and close the window. Then go to "System -> Administration -> Update Manager" and update your system (make sure to click "Check" to update the software sources). Reboot and let us know if you continue to have problems. :popcorn:

---

### Post by zrandyc on 2009-07-24
I performed the update but still could not connect. I turned the SSID broadcasting on and off several times and finally got a connection. We'll see if it holds. Next step will be to figure out how to get Ubuntu to see the hidden network, as that's something I value in this neighborhood. Thanks!

---

### Post by jaikenone on 2009-11-09
Fix for me was make the network visible, connect, then hide the network again.  I now connect automatically to the hidden network.

Regards.

---

### Post by xtek0 on 2009-12-26
I have a NC6220 and Installed NBR, the fix for me was to install, then remove the driver. Finally install it again, I was able to find available networks. :)

---

