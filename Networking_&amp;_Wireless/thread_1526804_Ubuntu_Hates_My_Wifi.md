---
title: "Ubuntu Hates My Wifi"
date: 2010-07-08
forum: Networking &amp; Wireless
---

### Post by Geek9 on 2010-07-08
So here's the deal I'm on a Dell Inspiron 1525, with intel 3945 ABG wifi card (built in) running the latest ubuntu 10.04. I'm trying to connect to a linsys WRK54G (broadcasting in B mode only) on channel 10 using a WPA Pre shared key with (with TKIP algorithm), however no matter what my ubuntu will not connect to the wifi (it works with other wifi), so in short anyone have any fixes? If not I'm going to try to use my vista wifi driver (vista connects fine, dualbooting btw), but I need help on how to switch drivers. Also I've triple checked the wifi passcode its right.

---

### Post by Geek9 on 2010-07-09
necessary bump is necessary

---

### Post by Easy Limits on 2010-07-09
Have you tried disabling your UFW/GUFW firewall?

---

### Post by Geek9 on 2010-07-10
> **Easy Limits said:**
> Have you tried disabling your UFW/GUFW firewall?
would a firewall really interfere with just connecting to a wifi? I could understand if it was all wifi points, but the more I think about it, it seems to me to be the security.
btw I'm looking for a program that lets me easily switch the drivers I use for my wifi

---

### Post by Geek9 on 2010-07-12
Well 2 days and a hell of a lotta research later and I have the goods. It appears I was right about the wifi security, my particular broadcom chipset has trouble use the standard ubuntu driver for wifi when connecting to wpa. So I had to use ndiswrapper to install the driver, however, I was using a vista driver throughout my beginning process and that appeared to function incorrectly with ndiswrapper prompting me to finally use a XP driver (but not before I had removed my network manager and had to use terminal to connect via ethernet, DOH) so here are the instructions to get this working on a dell insprion 1525 with intel 3945ABG chipset. First use this [http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper](http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper) (you can use terminal or synaptec to install ndiswrapper and the driver), however ignore the step about installing the driver (that driver does not work for 3945) instead use this [http://support.dell.com/support/downloads/driverslist.aspx?os=WW1&catid=-1&dateid=-1&impid=-1&osl=EN&typeid=-1&formatid=-1&servicetag=&SystemID=INS_PNT_PM_1525&hidos=WLH&hidlang=en&TabIndex=&scanSupported=False&scanConsent=False](http://support.dell.com/support/downloads/driverslist.aspx?os=WW1&catid=-1&dateid=-1&impid=-1&osl=EN&typeid=-1&formatid=-1&servicetag=&SystemID=INS_PNT_PM_1525&hidos=WLH&hidlang=en&TabIndex=&scanSupported=False&scanConsent=False) (grab the driver for whatever your wifi card is, in this case mine was the 3945). Once downloaded extract, then use ndiswrapper (it has a nice GUI) to locate the .inf file you need for your driver, if all goes well it will install and say hardware present. Continue that guide, but skip step 6 (not available in newer builds). Once you're finished (it should work fine, but if your network manager says your wifi device is not managed follow this last step), enter in terminal gksudo gedit /etc/NetworkManager/nm-system-settings.conf (it will open the .conf file and change [ifupdown] managed=false to true. Then bam you're done, working wifi with wpa supplicant.

---

