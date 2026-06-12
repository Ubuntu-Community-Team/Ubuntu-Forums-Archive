---
title: "Ubuntu 10.04 Lucid Lynx with ATT UVerse Wireless Networking"
date: 2010-07-15
forum: Networking &amp; Wireless
---

### Post by snookpup on 2010-07-15
Hi, I am new to Linux, but an old hand at Windows. I have just upgraded from Hardy Heron (8.04 LTS) to 10.04 LTS on CD from Canonical. I have a Dell Vostro A60,with clean 10.04 ONLY and no MS Windows. Wireless networking connected beautifully with my ATT UVerse Modem on 8.04, but will NOT connect now. Can anyone send me the Wireless Network Settings for 10.04, so I can WPA encript my wireless connection and connect to the internet? Right now, I cannot connect to the internet at all, but as stated, connected great to the internet on 8.04 LTS with WPA/WPA2 encrypion. 
 
Please help me with the settings, else I get stuck going back to 8.04, where at least I could connect.
 
This must be a simple task to some of you, but I cannot get the wireless connection to work at all with 10.04.  At&T set up the Uverse security as WPA/WPK
 
Brian F, Willowbrook, IL

---

### Post by bkratz on 2010-07-15
> **snookpup said:**
> Hi, I am new to Linux, but an old hand at Windows. I have just upgraded from Hardy Heron (8.04 LTS) to 10.04 LTS on CD from Canonical. I have a Dell Vostro A60,with clean 10.04 ONLY and no MS Windows. Wireless networking connected beautifully with my ATT UVerse Modem on 8.04, but will NOT connect now. Can anyone send me the Wireless Network Settings for 10.04, so I can WPA encript my wireless connection and connect to the internet? Right now, I cannot connect to the internet at all, but as stated, connected great to the internet on 8.04 LTS with WPA/WPA2 encrypion. 
 
Please help me with the settings, else I get stuck going back to 8.04, where at least I could connect.
 
This must be a simple task to some of you, but I cannot get the wireless connection to work at all with 10.04.  At&T set up the Uverse security as WPA/WPK
 
Brian F, Willowbrook, IL

Not totally sure what you need.  I (just recently ) logged into my new Uverse router  and set the encryption and password to what I wanted, not what they had. I changed to WPA2 with AES only and my password, so it is what it used to be (was using 9.04 before). 
I'll help if I can.

Brian

---

### Post by snookpup on 2010-07-15
Thanks Brian!  
 
I've been reading in some of these Ubuntu Dell-specific wireless threads that I may have to download some special Broadcom hardware driver that I may not have....I have to do something like...get into Terminal and execute some command to show me what type of wireless adapter I have (with Dell Vostro series shipped with 8.04 LTS only), and I suspect this will probably be the Broadcom adapter.  Then I have to install or invoke some driver program that was in 9.0 but not 8.0, which I missed going directly to 10.04 on the install CD from Canonical?  Gosh, I wonder why 10.04 would make wireless networking harder than an earlier version...I would expect it would have been easy.  Am I on the right tract with this Broadcom driver stuff?
 
Thanks for any help you can lend.  Is there an EZ way to do this?

---

### Post by bkratz on 2010-07-15
First we probably need to identify your wireless card. If you go to the terminal (applications>>accessories>>terminal) and type in


lspci -nn

and then

lshw -C Network

(those are LSHW in lowercase and C in upper  and LSPCI in lowercase)
and either look for the network controller or copy/paste the results back here.

If it is a Broadcom device (BCMxx) you can probably get it going with the following:

copied from an old posting by anewguy"

The best place to start is:

- temporarily hard wire your computer to the router
- in a terminal window:

sudo apt-get update

- then look in system/administration/hardware drivers and see if there is a driver list, and if so, be sure to enable it.

Wait a couple of minutes, then do the following:

- right-click on the network manager icon and be sure "Enable Wireless" is checked. If not, check it and close out of network manager and wait a couple of minutes.

- now left-click on the network manager icon and see if any wireless networks show.

"

---

### Post by snookpup on 2010-07-15
Thank You BK! I will do this and come back and let you know. I am on the thread on my windows computer, going back and forth to my Ubuntu 10.04 netbook.

---

### Post by snookpup on 2010-07-15
:oOK BK, here is what it said, and I think it IS a Broadcom adapter, and I will also try what you told me to do..wired directly to the router. 
 
[FONT=Calibri][SIZE=3]snookpup@snookpup-netbook:~$ lspci -nn[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][/SIZE][/FONT]
[FONT=Calibri][SIZE=3]00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GME Express Memory Controller Hub [8086:27ac] (rev 03)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][/SIZE][/FONT]
[FONT=Calibri][SIZE=3]00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][/SIZE][/FONT]
[FONT=Calibri][SIZE=3]00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][/SIZE][/FONT]
[FONT=Calibri][SIZE=3]00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][/SIZE][/FONT]
[FONT=Calibri][SIZE=3]00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][/SIZE][/FONT]
[FONT=Calibri][SIZE=3]00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][/SIZE][/FONT]
[FONT=Calibri][SIZE=3]00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][/SIZE][/FONT]
[FONT=Calibri][SIZE=3]00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][/SIZE][/FONT]
[FONT=Calibri][SIZE=3]00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][/SIZE][/FONT]
[FONT=Calibri][SIZE=3]00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][/SIZE][/FONT]
[FONT=Calibri][SIZE=3]00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][/SIZE][/FONT]
[FONT=Calibri][SIZE=3]00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][/SIZE][/FONT]
[FONT=Calibri][SIZE=3]00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][/SIZE][/FONT]
[FONT=Calibri][SIZE=3]00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][/SIZE][/FONT]
[FONT=Calibri][SIZE=3]00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][/SIZE][/FONT]
[FONT=Calibri][SIZE=3]00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][/SIZE][/FONT]
[FONT=Calibri][SIZE=3]02:00.0 System peripheral [0880]: JMicron Technology Corp. SD/MMC Host Controller [197b:2382][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][/SIZE][/FONT]
[FONT=Calibri][SIZE=3]02:00.2 SD Host controller [0805]: JMicron Technology Corp. Standard SD Host Controller [197b:2381][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][/SIZE][/FONT]
[FONT=Calibri][SIZE=3]02:00.3 System peripheral [0880]: JMicron Technology Corp. MS Host Controller [197b:2383][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][/SIZE][/FONT]
[FONT=Calibri][SIZE=3]03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][/SIZE][/FONT]
[FONT=Calibri][SIZE=3]04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][/SIZE][/FONT]
[FONT=Calibri][SIZE=3]snookpup@snookpup-netbook:~$ [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]lshw -C Network  (nothing happened)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
 
I will hook the Dell VOSTRO A90 notebook up to the router directly by wire, and try to do those commands you gave me.
 
Thanks. I will post what happens.
 
Brian (snookpup)

---

### Post by snookpup on 2010-07-15
OK Brian, (BK)-
 
I have connected by wire to the modem/router, and downloaded the Broadcom driver file, and enabled the driver, as you suggested. (By the way, it is I think, the B34 driver, and it is activated (the green neon screen light is lit for "driver activated")
 
In the 2WIRE579 (AT&T) wireless network settings, I entered the SSID, INFRASTRUCTURE, (No BSSID, I douldn't find one to enter), the MAC address, and I left MTU as Automatic.
 
For wireless security, I have WPA and WPA2 Personal. and entered the router password. IPV4 is set to automatic, and IPV6 is set to Ignore. 
 
It still has no working wireless network alive. The wireless network is checked as ENABLED.
 
Any ideas?
 
Thanks so much for your help
 
Brian
(snookpup)

---

### Post by bkratz on 2010-07-15
> **snookpup said:**
> OK Brian, (BK)-
 
I have connected by wire to the modem/router, and downloaded the Broadcom driver file, and enabled the driver, as you suggested. (By the way, it is I think, the B34 driver, and it is activated (the green neon screen light is lit for "driver activated")
 
In the 2WIRE579 (AT&T) wireless network settings, I entered the SSID, INFRASTRUCTURE, (No BSSID, I douldn't find one to enter), the MAC address, and I left MTU as Automatic.
 
For wireless security, I have WPA and WPA2 Personal. and entered the router password. IPV4 is set to automatic, and IPV6 is set to Ignore. 
 
It still has no working wireless network alive. The wireless network is checked as ENABLED.
 
Any ideas?
 
Thanks so much for your help
 
Brian
(snookpup)


Can you go to the terminal and post the output received from the command

```
sudo iwlist scan
```

The sudo will require your password which will not be echoed when you enter it, just press "Enter" when the command is put in.


You might also post the output of 

```
sudo lshw -C network > hardware.txt
```

Then you will find a text document in your /home/user directory, in this case hardware.txt, which you can drag-n-drop onto a flash drive and see it in Windows with wordpad and post it here, since you going between systems. You could also "pipe" the other command similarly to another file with the > for ease or just leave off the > hardware.txt if you don't want to do it that way. You do need to do these with the ethernet cable disconnected since network manager will use it if plugged in to ethernet. If you don't want to post the first one--do you "see" local A/P's?

---

### Post by snookpup on 2010-07-16
BK, (Brian), 
You are the Ubuntu Master, one of great wisdom.  I did exaclty as you had said in your first set of instructions, updated the Broadcom (B4) driver, rebooted, and at first, nothing STILL happened.  But then,after reconnecting my cable to the router to rejoin this forum, V 10.04 seemed to know somehow that it was missing a bunch of updates, and a window came up advising to use update manager, and it downloaded like over 100 updates to 10.04.  It took like a half hour to install them all.  Then I rebooted, put in my wireless network settings using 2WIREXXX as my id, with my router password, and opted for the same settings as 8.04 (infrastucture network), WPA/WPA2 security, entered all that info off the bottom of the modem/router, rebooted, and BINGO, the thing began finding every ATT network in my neighborhood (about 10 of them), plus a few other wireless networks.  I clicked mine to connect, and in like 2o sec I was ON!

Thank you Brian, for all your kind help.  I will pour you a giant Venti hot cup of UBUNTU Caramel Latte!

Thanks again....I now feel somewhat less powerless with this stuff.  You've helped me in my quest to be Windows FREE!

Brian
(snookpup):KS

---

### Post by bkratz on 2010-07-16
Well, it is always nice to wake up to good news. congratulations! Now the only thing left to do is go to the thread tools and mark the thread [solved] in case it helps someone else.

---

### Post by snookpup on 2010-07-16
Brian-
 
OK, yes, agreed, and thanks again....Do I mark this solved, or do you?:KS
 
The "other Brian"
snookpup

---

### Post by bkratz on 2010-07-16
You have to do it, I can't from here.

---

### Post by cdmccreary on 2011-08-20
I have a similar problem and the need to load 9.04 from CD.  Then to get on the wireless which is ATT Uverse.  Windows computers have no problem getting on the network.
 
I normally use WPA TKIP on 802.11g.  It never works on my ATT 2wire router but has no problem with a cheap Frys Wireless G router.  I can see all the ATT wireless networks in my area.
 
Any clues.

---

