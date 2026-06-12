---
title: "neither ath5k nor madwifi working in jaunty with atheros 5007eg"
date: 2009-07-24
forum: Networking &amp; Wireless
---

### Post by husunzi on 2009-07-24
I've got an Atheros 5007EG on a Toshiba Satellite L315. When I installed Intrepid (Ubuntu 8.10) on this, the wireless wouldn't work, & installing madwifi didn't solve the problem. The fix I eventually found was to install linux-backports-modules-intrepid-generic, after which “Support for 5xxx series of Atheros 802.11 wireless LAN cards” showed up under system>admin>hardware drivers, which I then enabled, after disabling the other option ("Support for Atheros 802.11 wireless LAN cards"). (I learned this from [here]("http://unsharptech.com/2008/10/31/atheros-wireless-in-ubuntu-810-intrepid-ibex/").) This allowed me to use wireless most of the time, although there were still occasions when it didn't work for some mysterious reason. 

I recently upgraded to Jaunty (Ubuntu 9.04, using the update manager, not a clean install), & when I did both the "Support for 5xxx..." & the original "Support..." options disappeared from the list of drivers, to be replaced only by the single option "Alternate Atheros "madwifi" driver," which was not activated. Since wireless was not working, I tried to activate madwifi, but its status just changed to "This driver was just disabled, but is still in use," & when I rebooted, madwifi went back to "not activated." [This tutorial]("http://ubuntuforums.org/showthread.php?t=1146020") helped me to figure out that ath5k, the default driver, was already installed, but since it wasn't working, I followed the directions there to blacklist ath5k under "/etc/modprobe.d/", un-blacklist madwifi (ath_pci) (I noted that ath_hal was already blacklisted - I haven't changed this), & download madwifi-tools. After this, I was able to enable madwifi under drivers, but it still didn't allow me to use wireless. In fact, with ath5k at least the "enable wireless" option appeared in the network manager (of course I made sure it was enabled), whereas with madwifi this option disappeared. 

I should also note that there is not a problem with the wireless service itself - I can access it with no problem from another computer using windows.

I wish I could just re-install the "Support for 5xxx..." driver, since at least that worked most of the time, but when I sudo apt-get install linux-backports-modules-intrepid-generic (or modules-jaunty or modules-jaunty-generic), I just get the message "linux-backports-modules-intrepid-generic [or jaunty, or jaunty-generic] is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded." 

Is there another driver I should try using? Or perhaps ath5k will work if I tweak something? (Remember, at least ath5k gave me an "enable wireless" option in the network manager, along with the options to find hidden connections & add new ones - of course I tried both of these options but they didn't work.) Or is there something else I'm missing or misunderstanding?

Thanks for your help. Please put any instructions in as simple terms as possible :)

---

