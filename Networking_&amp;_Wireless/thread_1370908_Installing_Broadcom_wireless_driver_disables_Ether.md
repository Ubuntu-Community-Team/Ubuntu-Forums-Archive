---
title: "Installing Broadcom wireless driver disables Ethernet"
date: 2010-01-02
forum: Networking &amp; Wireless
---

### Post by musicaldolphin on 2010-01-02
I have a Dell Inspiron E1505, which has the Dell Wireless 1505 (Broadcom) card.  To run the card, I installed the Broadcom STA wireless driver, which seems to activate the wireless card OK.  The problem is that once I installed that driver my onboard Ethernet card was deactivated (and yes, it is enabled in BIOS).  I had to remove the wireless driver to get the Ethernet back.  Does anyone have ideas?  I haven't found this problem listed elsewhere.  I am running Ubuntu 9.04 with no other problems.

---

### Post by Urnso on 2010-01-02
I had the same issues on an upgrade from 9.04, my broadcomm card would simply not work. I reinstalled a fresh 9.10 and still could not get my wireless to work. 

My fix was to go wired after installation and go to synaptic and totally remove the following packages:
bcmwl-kernel-source
bcmwl-modaliases

Reboot and make sure your wired connection comes up after reboot. 

Go back into synaptice reinstall those 2 packs, reboot and your wireless should work now. 

Worked for me, if you don't have wired I am sorry I don't know how to do this off USB or CD.

Good Luck!:P

---

### Post by musicaldolphin on 2010-01-03
My fix was to go wired after installation and go to synaptic and totally remove the following packages:
bcmwl-kernel-source
bcmwl-modaliases

Reboot and make sure your wired connection comes up after reboot. 

Go back into synaptice reinstall those 2 packs, reboot and your wireless should work now. 

Worked for me, if you don't have wired I am sorry I don't know how to do this off USB or CD.

Good Luck!:P[/quote]

I have wired when I removed the STA driver.  I looked for the packages you mention but they are not present in Synaptic.  Should I perhaps reinstall the driver, then remove them?

---

### Post by bkratz on 2010-01-03
Here is an alternate

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

The bcmwl.......  is on the live cd also.

---

### Post by musicaldolphin on 2010-01-03
> **bkratz said:**
> Here is an alternate

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

The bcmwl.......  is on the live cd also.

The driver is present in the Hardware Drivers applet.  My problem is that as soon as I activate the STA driver, my Broadcom wireless card is then recognized, but my Ethernet is disabled at that point.  I have to deactivate the STA driver to get my Ethernet back.

---

### Post by fxer on 2010-07-13
Any luck fixing this one? With a clean install of 10.04 when I enable wireless via that STA driver my wired disappears...

---

