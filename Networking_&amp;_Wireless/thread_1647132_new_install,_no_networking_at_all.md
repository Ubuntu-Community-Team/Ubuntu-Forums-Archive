---
title: "new install, no networking at all"
date: 2010-12-16
forum: Networking &amp; Wireless
---

### Post by fedu on 2010-12-16
I recently did a whole system wipe and got rid of windows all together!! Unfortunately, that means I have to start over with the whole networking thing. I know I have a bcm4311, but I have no idea what I have for a wired adapter. I know that I could search through everything to find what I need, but there is so much info for all the different versions. I have ubuntu studio. Can someone tell me the commands to type into the terminal to find out what I have for the wired network card and recommend a place to get the proper "drivers" to get my computer working again?


Thanks!

---

### Post by AgentZ86 on 2010-12-16
Maybe this will help:

For some reason Ubuntu won't let me post the link
Anyhow google search for bcm4311 on ubuntu 10.10
There is a zillion things people do to get them working.

But also remember you can look through the synaptic manager and search for those packages that are recommended to install the driver.

And check System/Administration/Extra Drivers that might find your drivers automatically.

---

### Post by AgentZ86 on 2010-12-16
Try here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by fedu on 2010-12-17
still nothing. I don't have wired support on the laptop and I think it  would be easier to fix the wireless problem if I had wired support. I  followed the actions on the [https://help.ubuntu.com/community/Wi...Driver/bcm43xx ]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")
page for the b43 driver and b43-fwcutter with no internet access by  copying the needed files to a flash drive and moving them over that way.  After a reboot, I still have no wireless. Is there a command that I'm  missing or something? Before I did the clean sweep and got rid of Vista,  I was running lucid as a secondary OS and went through the steps to  install b43 and fwcutter and it ended up working fine. However, my wired  card worked fine upon initial installation last time... this time it  does not.

I'm a bit lost with what to do right now.:confused:

---

### Post by fedu on 2010-12-17
.

---

### Post by fedu on 2010-12-17
Super strange - I looked through the live usb directory and clicked on pool>n>network-manager and opened all of the files inside and then rebooted. Update manager came up after reboot and downloaded 307 new updates. this is still a little quirky, but it seems to be working and I should be able to fix whatever else isn't right, now that I have internet.

---

