---
title: "Cannot Access Wireless Internet"
date: 2009-03-29
forum: Networking &amp; Wireless
---

### Post by enteef89 on 2009-03-29
Hello.  I am completely new to Linux altogether.  I have just installed Ubuntu 8.10 to my laptop.  I have no problems except connecting to my wireless internet.  I am currently using wired internet, but I would like to access my internet from wherever like before.  

I do not understand the whole command line business yet, and I have read about Network Manager.  I cannot figure out how to install it from the directory.  My laptop has a button that would turn the wireless adapter on and off, but it no longer works with Ubuntu.  Please help me.

Thanks.

---

### Post by enteef89 on 2009-03-30
bump

---

### Post by jelle_ on 2009-03-30
i need to know something more before i can help you. do you know what computer you use (manyfacturer, model, etc)?

can you enter the following command in a terminal:
lspci -v | grep Ethernet

---

### Post by enteef89 on 2009-03-30
This is what I got from the command:

02:05.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

And I'm not sure about what my computer really is actually.  I got it for christmas a few years ago, some nascar promo thing (and I hate nascar..) all I see is a sticker saying AMD Turion 64

---

### Post by enteef89 on 2009-03-30
Also I have read something about installing madwifi but I cannot figure out how to install it.  This is a big change from Windows.. but I am determined to learn.

---

### Post by jelle_ on 2009-03-30
an explanation on installing madwifi can be found here
[http://ubuntuforums.org/showthread.php?t=902860](http://ubuntuforums.org/showthread.php?t=902860)

follow the instructions in the sixt post

---

### Post by enteef89 on 2009-03-30
I am still having trouble.  I have installed madwifi, but I cannot turn on my wireless.  Ath0 cannot find anything, I don't think it is really working.  What do I do?

I am wondering if madwifi really did install properly.  How can I be sure?

---

