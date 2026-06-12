---
title: "How do I get my USB ADSL modem working"
date: 2006-01-09
forum: Networking &amp; Wireless
---

### Post by jacquesb on 2006-01-09
I am using an USB DSL modem (e-tech-V2 usb), using DHCP (not PPP). I have found some drivers that have to be installed, but I have no clue on how or what to do.

The drivers are:
/drivers/usb/atm/cxacru.c
/drivers/usb/atm/Kbuild
/drivers/usb/atm/Kconfig
/drivers/usb/atm/usbatm.c
/drivers/usb/atm/usbatm.h

Do I have to rcompile the kernel? If yes, do I need the sources (linux-tree, kernel-package), etc. If yes, they d ar not on the installation CD, and I canot download (with ubuntu, as I have no internet-conection).

Or is there an easier way?

Thanks for any comment.

---

### Post by GA\/1N on 2006-01-09
yes i suffer the same fate as you. I have AOL bb and it uses a USB DSL modem. This will not work at all, apparently you should buy a router and an ethernet cable to connect to the internet.

---

### Post by GA\/1N on 2006-01-09
What internet company are you with

---

### Post by healychan on 2006-01-10
I believe that USB modem wouldn't work with Ubuntu. I was having the same problem as you and I ask for advice from my tutor (I am a computing student). He said that I need to get an ethernet modem, or router.

---

### Post by GA\/1N on 2006-01-10
Quote what i said.:confused:

---

### Post by jacquesb on 2006-01-11
[QUOTE=GA\/1N]What internet company are you with[/QUOTE]
Versatel in the Netherlands

---

### Post by jacquesb on 2006-01-11
[QUOTE=healychan]I believe that USB modem wouldn't work with Ubuntu. I was having the same problem as you and I ask for advice from my tutor (I am a computing student). He said that I need to get an ethernet modem, or router.[/QUOTE]
I found a thread in a Dutch forum where somebody claimed he got this E-tech modem working with the drivers I mentionded, and by recompiling the kernel (2.10-386). 

I have found some things I haven't tried yet on:
[https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto)

I will work on it and post the result (in a few days)

---

### Post by jacquesb on 2006-01-20
[QUOTE=healychan]I believe that USB modem wouldn't work with Ubuntu. I was having the same problem as you and I ask for advice from my tutor (I am a computing student). He said that I need to get an ethernet modem, or router.[/QUOTE]

I have got it running:
in short:
1. you have to get usbatm and cxacru (+makefiles etc.) from sourceforge
2. the kernel needs to be recompiled, replace the old usb_atm and add cxacru + makefiles in the drivers/usb/atm section of the source
3. you need to get the firmware of the modem that cacru will upload 
4. restart - if everything went well the modem may indicate it got a conection (you can also check the systemlog to see the messasges from cxacru)
6. you have to get the br2684ctl package from an debian archive (it is not in the ubntu-archive)
6. you have to type some magic words in a terminal window:
modprobe 2684
br2684ctl -b -c 0 -a (followed by a provider  dependent code, in my case: 0.0.32)
dhclient nas0 (ubuntu equivalent of dhcpcd)

It worked for me, although I got a few warning-messages at the end)

It was still difficult because:
- the ubuntu CD does not contain the required packages, so I have switched for more than 20 times between Eindows and Ubuntu (reboot, reboot, reboot)
- most 'recpies' are incomplete, you have to check out many forums
- most 'recepies' are for debian, ubuntu has sometimes different comands (such as dhclient instead of dhcpcd)

---

### Post by nalsur on 2007-03-07
> **jacquesb said:**
> I am using an USB DSL modem (e-tech-V2 usb), using DHCP (not PPP). I have found some drivers that have to be installed, but I have no clue on how or what to do.

The drivers are:
/drivers/usb/atm/cxacru.c
/drivers/usb/atm/Kbuild
/drivers/usb/atm/Kconfig
/drivers/usb/atm/usbatm.c
/drivers/usb/atm/usbatm.h

Do I have to rcompile the kernel? If yes, do I need the sources (linux-tree, kernel-package), etc. If yes, they d ar not on the installation CD, and I canot download (with ubuntu, as I have no internet-conection).

Or is there an easier way?

Thanks for any comment.

where u get this all driver?
i want it for my ubuntu 6.1 adsl usb modem

thankz

---

