---
title: "Weak wifi-signal on HP Pavillion G6"
date: 2012-02-08
forum: Networking &amp; Wireless
---

### Post by hexwind on 2012-02-08
Hello everyone,
I've been using Ubuntu since years now until i purchased my new HP G6 12XX pavillion.
The wifi network on Windows Seven works without a problem. But once Ubuntu, the signal is very weak. When i'm not in the room where my rooter is, it can't even connect to the internet, on Windows Seven it does tho ! Did anybody encounter the same problem before? I had this problem on Ubuntu 11.10 and now I'm installing Ubuntu 11.04 as we speak, and same thing happen (but from the CDBoot though)

---

### Post by ianchai on 2012-02-15
> **hexwind said:**
> Hello everyone,
I've been using Ubuntu since years now until i purchased my new HP G6 12XX pavillion.
The wifi network on Windows Seven works without a problem. But once Ubuntu, the signal is very weak. When i'm not in the room where my rooter is, it can't even connect to the internet, on Windows Seven it does tho ! Did anybody encounter the same problem before? I had this problem on Ubuntu 11.10 and now I'm installing Ubuntu 11.04 as we speak, and same thing happen (but from the CDBoot though)

I have a HP Pavilion G4-1212TU and have the exact same problem!

Been struggling with this laptop since I got it trying to put it in LINUX! I hope I don't have to switch back to Windows!!!

---

### Post by AlanR8 on 2012-02-15
Could do with a bit more information about the network card and installed driver.

Whilst not an answer, I had a similar situation with an old HP Pavillion laptop so I went out and bought a USB network card for about £17.00. About the size of a thumb nail, no software required, plugged it in and bingo problem solved.

---

### Post by ianchai on 2012-02-15
> **AlanR8 said:**
> Could do with a bit more information about the network card and installed driver.

Is this the information you need?

$ lspci -nnk |grep -i net -A2
01:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
[INDENT]Subsystem: Hewlett-Packard Company Device [103c:1795]
	Kernel driver in use: brcmsmac[/INDENT]
--
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
[INDENT]Subsystem: Hewlett-Packard Company Device [103c:166d]
	Kernel driver in use: r8169[/INDENT]

> **AlanR8 said:**
> 
Whilst not an answer, I had a similar situation with an old HP Pavillion laptop so I went out and bought a USB network card for about £17.00. About the size of a thumb nail, no software required, plugged it in and bingo problem solved.

I'm a university lecturer in a third-world country so I'd rather not have to spend another RM 80 if I can avoid it :(

Thanks.

---

### Post by ts3 on 2012-02-15
> **ianchai said:**
> Is this the information you need?

$ lspci -nnk |grep -i net -A2
01:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
[INDENT]Subsystem: Hewlett-Packard Company Device [103c:1795]
	Kernel driver in use: brcmsmac[/INDENT]
Thanks.

Your wireless card is BCM4313 and the brcmsmac driver won't work for this particular chipset.  The wl (this is WL) driver works, you can get it from the Ubuntu Software Centre by typing bcmwl in the search box and downloading the three drivers that pop up.  You'll also need to remove and blacklist the brcmsmac driver and any other conflicting drivers, such as b43 and bcma, that you might end up loading inadvertently while troubleshooting.  

The readme.txt file from Broadcom's website at [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
has a good explanation on conflicts and blacklisting (check the "Fresh Installation" bit).  

If you search the ubuntu forums I'd suggest searching for BCM 4313 rather than using more general search terms such as Broadcom.  I posted a step-by-step (warning: long post) solution that worked for me a while back.  Sorry, I don't know enough to be more specific, I can just point you in the right direction.

Cheers :)

---

### Post by ianchai on 2012-02-16
Thanks for your suggestion. I also just found [http://askubuntu.com/questions/83262/broadcom-4313-signal-strength-very-low-on-an-hp-pavilion-dv4](http://askubuntu.com/questions/83262/broadcom-4313-signal-strength-very-low-on-an-hp-pavilion-dv4) which suggested switching to the older 2.6.39.2 kernel seems to work... not sure why a kernel switch would help.

Your suggestion makes more sense, so I plan to try your suggestion first, and if it doesn't work, then try the kernel switch suggestion...

---

### Post by ianchai on 2012-02-16
Thanks very much, ts3! I googled for your name and BCM 4313 and found [http://ubuntuforums.org/showthread.php?t=1889170](http://ubuntuforums.org/showthread.php?t=1889170) which gave me the information I needed to solve my problem!

---

### Post by ts3 on 2012-02-16
> **ianchai said:**
> Thanks very much, ts3! I googled for your name and BCM 4313 and found [http://ubuntuforums.org/showthread.php?t=1889170](http://ubuntuforums.org/showthread.php?t=1889170) which gave me the information I needed to solve my problem!

Glad it's all sorted out and glad I was able to help :) There are other posts on the forums with the same/similar solution so pointing people in the right direction (chipset 4313 and wl driver) usually works but I am glad that what I posted is of use to other people.

Cheers :)

---

### Post by ianchai on 2012-02-16
> **ts3 said:**
> Glad it's all sorted out and glad I was able to help :) There are other posts on the forums with the same/similar solution so pointing people in the right direction (chipset 4313 and wl driver) usually works but I am glad that what I posted is of use to other people.

Cheers :)

I guess I couldn't find them because I didn't know the right question to ask. I searched based on my PC model name & number :P

---

### Post by ts3 on 2012-02-16
> **ianchai said:**
>  I searched based on my PC model name & number :P
Yep, same thing I did a couple of months ago.  I ended up trying solutions from every post that had the words "hp" or "Broadcom" in it so had all sorts of driver conflicts.  

At the time I was quite exasperated but with hindsight it's been quite a useful learning experience.  It gave me the confidence to use the terminal and a basic understanding of how linux works.  So not all bad after all :)

---

### Post by ianchai on 2012-02-16
> **ts3 said:**
> Yep, same thing I did a couple of months ago.  I ended up trying solutions from every post that had the words "hp" or "Broadcom" in it so had all sorts of driver conflicts.  

At the time I was quite exasperated but with hindsight it's been quite a useful learning experience.  It gave me the confidence to use the terminal and a basic understanding of how linux works.  So not all bad after all :)

The ironic thing is that I'm quite familiar with the command-line terminal as I've been using UNIX or LINUX for **years**! (I have a 1998 Compaq desktop PC running Red Hat that is **still** working after all these years :)!) But I never tried to configure the WiFi before. 

Previously, I'd been using LINUX on desktop PCs with wired connections, and then for my previous laptop, a Dell Inspiron 1420, WiFi just worked automatically after I installed Ubuntu with no modifications.

---

