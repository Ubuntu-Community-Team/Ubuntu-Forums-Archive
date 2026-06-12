---
title: "Cant see wifi"
date: 2012-10-15
forum: Networking &amp; Wireless
---

### Post by douggiephresh on 2012-10-15
I just installed xubuntu 12.04 on my dell inspiron 1501 laptop. Additional Drivers recommended the Broadcom STA wireless driver, so I installed it but it still doesnt see my wifi network. How do I fix this?

---

### Post by douggiephresh on 2012-10-15
any ideas? i read the sticky but it still isnt working.

---

### Post by douggiephresh on 2012-10-15
Okay, I think the problem is that my wifi card is disabled. I can see that the "wifi" light on the laptop isnt on. How do i turn on my wifi card and get the light to turn on? I dont dual boot windows and I have read all the literature on installing the drivers and everything pertaining to my wireless card (BCM 4311 14e4:4311) but I dont see anything about getting the light to turn on.

---

### Post by sandyd on 2012-10-15
Do you have a 'wifi switch' by any chance on your laptop?

---

### Post by douggiephresh on 2012-10-15
solved. 

I am  going to install the correct driver for this wireless card. Then I will remove the &#8220;incorrect&#8221; driver (bcmwl) which Ubuntu installed by default.

$ sudo apt-get update
$ sudo apt-get install firmware-b43-installer
$ sudo apt-get remove bcmwl-kernel-source
$ sudo reboot

---

### Post by bkratz on 2012-10-15
> **douggiephresh said:**
> Okay, I think the problem is that my wifi card is disabled. I can see that the "wifi" light on the laptop isnt on. How do i turn on my wifi card and get the light to turn on? I dont dual boot windows and I have read all the literature on installing the drivers and everything pertaining to my wireless card (BCM 4311 14e4:4311) but I dont see anything about getting the light to turn on.


Post two here will solve your problems unless we have to remove any blacklists of b43 that were created by using the STA driver.

[http://ubuntuforums.org/showthread.php?t=1997880](http://ubuntuforums.org/showthread.php?t=1997880)

You might also post the output of

sudo rfkill list all

so we can look for blockages.

---

