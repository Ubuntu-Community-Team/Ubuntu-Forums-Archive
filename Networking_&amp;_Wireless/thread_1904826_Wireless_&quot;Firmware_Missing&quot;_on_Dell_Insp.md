---
title: "Wireless &quot;Firmware Missing&quot; on Dell Inspiron Mini 10 Netbook"
date: 2012-01-05
forum: Networking &amp; Wireless
---

### Post by derekmartin81 on 2012-01-05
I'm very new to Ubuntu (installed it yesterday) but I'm running into problems getting wireless to work.  I see similar posts on here but there's a lot of wording I don't understand and need to be walked through.
 
I've used Windows machines all my life and I finally have the chance to mess with Ubuntu since I have my wife's old netbook to play with.
 
Any help is greatly appreciated.

---

### Post by MARP1961 on 2012-01-06
Get your hands on an ethernet cable long enough to plug your laptop directly into your router. Reboot and you should have a dependable, wired connection with no need to enter WEP or WPA keys.

Next thing to do whilst connected is to open Update Manager and let it do all the updates. Now to get wifi working you almost certainly need to install a driver that may not be included on the install CD. My guess is that it is a Broadcom wifi.

With the ethernet connection fully working, try opening up the Additional Drivers application to see if it lists anything to install. Install the driver it finds,** reboot without the cable in** and then left click the wifi icon to see if your router is listed. if it is, you should be able to select it and enter your WEP or WPA passkey the same as in Windows.

If you are offered the STA driver or the B43 driver there seem to be issues with the wrong one being installed first then blacklisting the other so that it cannot be installed later. I needed the B43 one for my son's Dell.

---

