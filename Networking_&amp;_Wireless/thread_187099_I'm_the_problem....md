---
title: "I'm the problem..."
date: 2006-06-02
forum: Networking &amp; Wireless
---

### Post by asdf38 on 2006-06-02
ok right so I don't know much about anything but I installed ubuntu back in november and haven't used it cause I didn't have time to do anything now that it's the summer I can start to play with it... 

this is my prob. I don't know anything about ubuntu and I need to get my wireless up can anybody tell me step by step exactly what I need to do,,,? this is what I have... Acer InviLink wireless LAN network connection 802.11b/g 
thanks

---

### Post by asdf38 on 2006-06-02
I found this on the ndiswrapper site but it makes no sense to me if anybody can help please take a sec to give me some directions...

Laptop: Acer Ferrari 3400LMi

    * Chipset: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
    * Other: Much like all the other Broadcom/Acer cards, but won't scan/work right unless you set the boot options "apm=off acpi=noirq" in /boot/grub/menu.lst so that the kernel starts up that way. Tested with SuSE 9.1 (with SuSE 9.2 2.6.8 kernel security fix rpm as an easy way to upgrade to more recent kernel) and ndiswrapper 1.1rc2, using Acer broadcom driver. The "apm=off" allows the proprietary driver to exit without hanging the unit, too =O)

---

### Post by jobezone on 2006-06-02
Yes, that piece of text is a bit mangled. Here, let me clean it up for you:

- Set the boot options "apm=off acpi=noirq" in /boot/grub/menu.lst 

- Tested with SuSE 9.1, and ndiswrapper 1.1rc2, using Acer broadcom driver.

I just cleared up the text, I don't know if this is the correct way for you to have wireless. If you indeed have a broadcom chipset, then follow this guide [https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx](https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx) from ubuntu's wiki, since ndiswrapper is no longer needed for this chipset, and there is a simpler method.

---

### Post by ubuntu27 on 2006-06-02
I think asdf38 is using Breezy and not Dapper. 

> 
I installed ubuntu back in november and haven't used it 

---

