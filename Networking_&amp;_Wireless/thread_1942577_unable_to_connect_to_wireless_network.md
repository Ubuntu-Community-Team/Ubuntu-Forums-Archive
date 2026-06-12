---
title: "unable to connect to wireless network"
date: 2012-03-17
forum: Networking &amp; Wireless
---

### Post by usernew on 2012-03-17
Hi All,

I am new to linux/Ubuntu and need some help!

I have a new Dell Precision M6400 core I7 laptop. i am not able to connect to wireless network. 

i tried all options in the config guide but still was not successful. In the additional Drivers window i see that it is using Broadcom STA wireless driver. I can see my SSID but  just cannot connect to it.

when i do sudo lshw -C network i get this?
 *-network
                description: Wireless interface
                product: BCM4313 802.11b/g/n Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0


What am i doing wrong ?? please help.

Thanks

---

### Post by ts3 on 2012-03-17
> **usernew said:**
> when i do sudo lshw -C network i get this?
 *-network
                description: Wireless interface
                product: BCM4313 802.11b/g/n Wireless LAN Controller

Hi, your Broadcom card is BCM4313 which needs the wl (WL) driver to work well.  The brcmsmac, b43 and bcma drivers do not work well/at all with 4313 unfortunately.  If you enter in terminal

```
lspci -k
```

and look towards the end of the output you will see Broadcom BCM4313 and then under it it will tell you which driver is in use and which modules are loaded.  

I'd suggest uninstalling/de-activating the STA drivers and any other such as b43 that you might have installed and then installing the wl driver from the Ubuntu Software Centre by typing "bcmwl" in the search box and installing the two drivers that come up.  You can also use the Ubuntu Software Centre to check for and uninstall any b43 drivers you might have.  Reboot.  

If that doesn't work make sure to use BCM4313 as a search word, there are plenty of threads on the forums such as this one: [http://ubuntuforums.org/showthread.php?p=11380687](http://ubuntuforums.org/showthread.php?p=11380687) with more detailed or less detailed explanations on getting wireless to work with BCM4313 (sometimes people need to remove/blacklist conflicting drivers which is fairly easy to do).

Good luck and post back what works and what doesn't.

Cheers :)

P.S. I am assuming you installed 11.10

---

