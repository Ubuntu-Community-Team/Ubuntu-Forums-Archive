---
title: "How to get Atheros WiFi working in 9.10"
date: 2010-02-10
forum: Networking &amp; Wireless
---

### Post by SteveMRose on 2010-02-10
When I upgraded to 9.10 from 9.04, my D-Link atheros WiFi card stopped working. I previously had madwifi installed in 9.04 but upon upgrading told Ubuntu to remove all non-used programs and besides, madwifi for 9.04 will not work in 9.10.

So, after searching around in all sorts of forums, I found a fix, and here it is step-by-step for those of us who are not Linux mavens.

1. open a terminal window and enter the following command:
sudo apt-get install linux-backports-modules-karmic

This will install the required driver for the atheros chipset and inactivate any madwifi remnants.

2. Now edit the blacklist files to allow the ath5 driver to be loaded. to do this:

open a terminal window and enter:
gksudo gedit

This will open gedit with administrator privileges. 

3. Click on "Open" and navigate to the \etc\modules.d folder.

4. One by one open all files with the name "blacklist" in it and add a "#" and a space before ath5, then save each file.

5. Close gedit

6. Close the terminal window.

7. Restart the computer.

Bootup will take a bit but the WiFi should now be active and connect to your WiFi if you had it configured in 9.04 or an earlier version of Ubuntu. If not (i.e.- this is a clean install of Ubuntu), then you will have to configure the connection using Network Manager or a substitute program that is available.

Hope this helps- it took me a while to figure this out. I have to say that until now Ubuntu has impressed me with the ease of updates and seamless working. This update, however, really messed things up and IMHO, someone was not thinking about the effect of changing a name of some internal header and the effect on those of us who use an atheros chipset and had madwifi installed.

steve

---

### Post by chili555 on 2010-02-10
> \etc\modules.dI believe this should be:```
/etc/modprobe.d
```

---

