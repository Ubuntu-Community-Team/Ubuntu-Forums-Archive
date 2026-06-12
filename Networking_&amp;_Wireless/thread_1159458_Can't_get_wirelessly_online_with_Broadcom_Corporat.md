---
title: "Can't get wirelessly online with Broadcom Corporation BCM4306"
date: 2009-05-14
forum: Networking &amp; Wireless
---

### Post by The Switch Blade on 2009-05-14
Hi,
 
I just came home from college and now need to use wireless internet in my home.
 
In the upper right hand corner, it recognizes no wireless connections. If I create a new connection and type in the SSID ("MARBLE") and the WEP (11e3005178) it tells me that "nm-connection-editor" wants access to the default keyring, but it is locked. So, I enter my password and I remain offline.
 
I have a Broadcom Corporation BCM4306 Belkin 7000.
 
In the docs, however, I see "The bcm43xx driver (via manual install) is now considered to be deprecated as it is now included in Ubuntu 8.04 and all Linux kernel versions 2.6.24 and later."
 
How can I get online?
 
My assumption is to follow the instructions in [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) . Can someone confirm this? I'm new to ubuntu and don't want to destroy everything.

---

### Post by divague on 2009-05-14
this might help you

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff")

---

### Post by The Switch Blade on 2009-05-14
Update:
 
I put in my ubuntu cd. The ndiswrapper-common package was corrupted and would not install. I downloaded them off of the ubuntu packages site. For some reason, it said that the AMD64 packages were incompatible, but the i386 packages weren't. I have an AMD64 processor... whatever.
 
So, I install those packages and get here:
 
"
<LI class=level1>[LIST=1]
[*]Card: Belkin 54g Wireless Desktop Network Card (F5D7000) Rev 03
[*]Chipset: BCM4306
[/LIST]
[LIST]<LI class=level2>pciid: 14e4:4320
<LI class=level2>Driver: [http://ftp.us.dell.com/network/R81433.EXE]("http://web.archive.org/web/20080101235828/http://ftp.us.dell.com/network/R81433.EXE") (use bcmwl5a.inf in directory AR)
<LI class=level2>Other: I tried to use the belkin driver (bcmwl5.inf) but the whole system just locked up as soon as I modprobed ndiswrapper. Apparently the belkin driver works for the older rev 02 cards, but not rev 03. So I&#8217;m suggesting this for folks with the Rev 03 card. You can check the revision by doing a &#8220;lspci&#8221; The Dell driver has been working great for me, for about a day.
[*]Other: The rev.03 problem is probably not all that sinister. It is caused by the presence of the NetworkType|0 line which ends up in the*.conf files (from the *.inf driver file). Removing this allows the supplied Belkin driver to work, although I&#8217;d probably recommend using the Dell R81433.exe driver anyway if only because it&#8217;s a later version. For non-US users you may wish to edit the Channel parameter to be 13 (Europe) (or 14 in Japan?). Applies to both PCMCIA and PCI versions (F5D7000 and F5D7010)."
[/LIST]So I download that and run it through wine. It unzips and I grab the inf file and put it in a folder. There's 3 sys files so I try each of them. Everything I try says "unable to see if hardware is present" and then when I press configure network it says there is "no network configuration tool" or something along those lines.
 
I tried to do the one above it with F5D7000-V2.4.5.EXE, but I get the EXACT same problem.
 
Should I uninstall my packages and try to install the amd64 ones even though it says that it is wrong? :/

---

### Post by cargman on 2009-05-17
> **divague said:**
> this might help you

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)


Sweet! thanks for the link!  Worked like a charm for me! 

(I have a dell inspiron 6000 with a Broadcom BCM4306 (rev03) )

---

