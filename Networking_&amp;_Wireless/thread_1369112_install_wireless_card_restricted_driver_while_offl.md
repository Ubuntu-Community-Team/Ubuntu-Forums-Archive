---
title: "install wireless card restricted driver while offline?"
date: 2009-12-31
forum: Networking &amp; Wireless
---

### Post by stldirty on 2009-12-31
hey so here's my problem.  i am dual booting windows 7 and ubuntu 9.10.  i'm currently using my iphone's tethering over wifi for internet.  i've found that my wifi card on my laptop won't work, however, until i install a restricted driver for it.  it seems as if i need an internet connection to download this driver though.  i don't have an ethernet line to download it from so thats out of the question.  is there anyway i can download the particular file from my windows 7 installation then reboot into ubuntu and install it that way?

also, is there a way to get the iphone's usb tethering to work?

thanks in advance.

---

### Post by bkratz on 2009-12-31
Check here and see if it is applicable for the device you have.

[http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865)

---

### Post by Mahngiel on 2009-12-31
depending on your wireless card, that link may not work. the bcmwl-kernel is for Broadcom cards version 4315+ (or somewhere near there) there are suitable work-around depending on your card.

Look at this thread, and help us help you by providing us with a bit more details please.
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by stldirty on 2009-12-31
its a bcm43xx card.  broadcom.  i'm in windows right now because thats the only thing i have internet.  if you need me to get more specific i'll go into linux and let you know.

---

### Post by Mahngiel on 2009-12-31
In windows, you should be able to Control Panel -> System -> Properties -> Find your wireless device and driver.

In Linux: Find your BCM version by typing code:
```

lspci -nn | grep 'Broadcom'

```I'll show you mine, and what things to look for
```
king@mahngiel:~$ lspci -nn | grep 'Broadcom'
02:03.0 Network controller [0280]: Broadcom Corporation [COLOR=Blue]BCM4306[/COLOR] 802.11b/g Wireless LAN Controller [[COLOR=Red]14e4:4320[/COLOR]] (rev 03)
```[COLOR=Blue]Broadcom[/COLOR] [COLOR=Blue]4306 = Chipset[/COLOR]
[COLOR=Red]14e4:4320 = PCI-ID[/COLOR]

Visit this[COLOR=DarkOrange] [[link]("http://linuxwireless.org/en/users/Drivers/b43")][/COLOR] and see if your version is supported, and follow the instructions. It may be useful to save the page to your flash drive, or you could write them down.  As far as the packages, just get rid of the 'wget' code behind the http:// address, and copy the link to your browser, you will be able to save them to your flash to install later.

If your BCM is a later version than is provided there, the BCMWL package should work. if you're afraid of trying to pull the package off the cd, check this [[link]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=bcmwl")]. that's the ubuntu package for the modalias and source package for it.  Those you can download as well, and linux should unpack and install them easily.

Hope this helps.

*Note: you may also browse the Networking & Wireless topic for your BCM number, and see what other people have done to get their card working.  Remember, you'll have to reboot after you install the packages*

---

