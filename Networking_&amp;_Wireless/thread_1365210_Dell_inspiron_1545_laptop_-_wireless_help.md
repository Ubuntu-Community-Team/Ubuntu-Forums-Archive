---
title: "Dell inspiron 1545 laptop - wireless help"
date: 2009-12-26
forum: Networking &amp; Wireless
---

### Post by linc186 on 2009-12-26
I recently got a dell inspiron 1545 laptop. It came with windows 7, and I dual booted it with ubuntu v9.10. I went to ubuntu.com, downloaded it, burned the image to a disk, put the disk in, rebooted the computer, installed ubuntu, everything went fine. The computer gives me the option between which operating system, ubuntu works fine, etc. But, as I was exploring the world of ubuntu 9.10, i realized that my wireless hadn't worked. When I clicked on my network manager, no options came up except for wired network, VPN, and disconnect which was written in gray, implying that you cant click on it. When i right clicked, the onyl things that came up were enable networking (which I have checked), something written in gray again, and edit connections. I surfed the forums for the answer, only to find but a few suggestions that either I did not understand, or just didn't work. One suggestion directed me to plug in an ethernet cable and do updates which should fix it, but, even with plugging in an ethernet cable, it still did not work. Also, i followed some console commands to find out what type of wireless card i have, i have a pci. If that helps at all. Also, in hardware drivers, no drivers or anything comes up at all, which i think is another key detail you need to help me. And, i have found threads that claim downloading a driver would help fix it, and they also supplied a link for download. I went to the website and read the read me, it meant nothing to me. I could not understand it at all. So, if you could maybe direct me through that, that would be a BIG help. I'm a new linux user, so forgive me for any obvious questions i have gave. Thanks a lot in advance!

-linc186.

---

### Post by gordintoronto on 2009-12-27
First, please make paragraphs.  [smile]

When you run the command lspci it should show you the brand and model for each PCI device, including your wireless adapter.  It is a PCI adapter, but you might need to know the brand and model.

Many wireless adapters "just work."  The device driver is built into Linux, you don't have to download or install anything.  If yours is one of these, what you want to do it "edit connections."  There should be a tab labelled "wireless," you click on "add."  You will need to know the ID of your router, the type of security, and the router's password.

If you plug in an ethernet cable between your router and your computer, then boot up, you should immediately have Internet access.  If you do this, what happens?

Here's a quick tutorial for adapters that "just work":
[http://www.pcmech.com/article/how-to-quick-wireless-setup-with-ubuntu-804/](http://www.pcmech.com/article/how-to-quick-wireless-setup-with-ubuntu-804/)

If your adapter is not one of these, you will need to learn about ndiswrapper.  I have never needed it, so I can't help you with it.

---

### Post by linc186 on 2009-12-27
> **gordintoronto said:**
> First, please make paragraphs.  [smile]

When you run the command lspci it should show you the brand and model for each PCI device, including your wireless adapter.  It is a PCI adapter, but you might need to know the brand and model.

Many wireless adapters "just work."  The device driver is built into Linux, you don't have to download or install anything.  If yours is one of these, what you want to do it "edit connections."  There should be a tab labelled "wireless," you click on "add."  You will need to know the ID of your router, the type of security, and the router's password.

If you plug in an ethernet cable between your router and your computer, then boot up, you should immediately have Internet access.  If you do this, what happens?

Here's a quick tutorial for adapters that "just work":
[http://www.pcmech.com/article/how-to-quick-wireless-setup-with-ubuntu-804/](http://www.pcmech.com/article/how-to-quick-wireless-setup-with-ubuntu-804/)

If your adapter is not one of these, you will need to learn about ndiswrapper.  I have never needed it, so I can't help you with it.


No, you don't understand. I have Broadcom BCM4312 card. I downloaded ndiswrapper and downloaded the needed driver for my card. I also found the .inf file for my windows driver, so i have all the needed files, but i don't know what to do with them! the tutorial read me that came with the driver download makes no sense to me! That's what i need help with. I didn't describe it well enough - sorry....

---

