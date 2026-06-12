---
title: "Building a driver?"
date: 2009-03-17
forum: Networking &amp; Wireless
---

### Post by Powerman2442 on 2009-03-17
Okay, my problem is I bought a PCI Wireless NIC that said it supported Linux. However, the driver they include is far from easy (for me) to install by myself. They have a "manual" included on their CD that tells you how to install. However, I still can't get it installed. Contacted the company and they said they don't "support" the driver they just put it on their CD. Read on for information on the folder name, files included, and a copy & paste directly from the "manual" (readme) they include on the CD. 

RTL8185_Linux_2.6_v1027.0823.2007

Files:
- ifcfg-wlan0
- makedrv
- readme
- rtl8185.ar.gz
- stack.tar.gz
- wlan0dhcp
- wlan0down
- wlan0up
- wpa_supplicant-0.4.9.tar.gz

The "readme" says...

RTL8185 Linux Driver v1027.0823.2007 for linux kernel 2.6

  - Support Client mode for either infrastructure or adhoc mode
  - Support WEP and WPAPSK/WPA2PSK connection

===============================================================================================
< Component >
The driver is composed of several parts:
    (1)source code
	rtl8185.tar.gz
	stack.tar.gz

    (2)Script ot build the modules
        makedrv

    (3)Script to load/unload modules
        wlan0up
        wlan0down

    (4)Script and configuration for DHCP
	wlan0dhcp
        ifcfg-wlan0

    (5)Supplicant source code
	wpa_supplicant-0.4.9.tar.gz
    	
    (6)Example of supplicant configuration file
	wpa1.conf




< Installation >
Running the scripts can finish all operations of building up modules from source code and start the nic:

	(1)Build up the driver from the source code
         	./makedrv

    	(2)Load the driver module to kernel and start up nic
    		./wlan0up
           (if "insmod: error inserting 'r8180.ko': -File exists." met,
	        ./wlan0rmv
		./wlan0down
		./wlan0up
	    should be OK.
	   )

I have tried running the scripts (running in terminal as well as just plain "Run") "makedrv", "wlan0up", and "wlan0dhcp" (in that order). I don't phsically see anything happening when I "Run" it. When I "Run in Terminal" and Terminal window pops up and saying a bunch of stuff then shuts down. I don't have time to read it.

Also, the wireless NIC I have is a Linkskey (NOT Linksys) LKW-G553. This "driver" comes on the CD with the Windows and Mac drivers. The reason I bought this card was because it had a Linux driver. Problem is it either doesn't work or I am not knowledgeable enough with Linux to install the driver. Also, the company doesn't really support the driver for Linux. I think they just include it on the CD to say "Works with Linux!"

I am useing Ubuntu 8.04 and currently posting this via Windows XP. I honestly wish I could just plain get rid of Windows and use Linux, but I don't see this happening anytime soon. :(

Let me know if you can help. And there is no way I can not use wireless on this PC. It is about 400 feet from my cable modem/Linksys router.

Thanks again,

---

### Post by chili555 on 2009-03-17
Do you have *linux-backports-modules-intrepid-generic* installed? It apparently has a newer rlt8180 driver. Perhaps that will work better.

---

### Post by Powerman2442 on 2009-03-17
> **chili555 said:**
> Do you have *linux-backports-modules-intrepid-generic* installed? It apparently has a newer rlt8180 driver. Perhaps that will work better.

Not exactly sure what that is. The Intrepid part leads me to believe that it is something that comes with 8.10.

Oh, and I am not even sure if what I am doing to make/build the driver is correct. The driver they give might work, not sure because I've never messed with anything like this up to this point.

---

### Post by gtr32 on 2009-03-17
> **Powerman2442 said:**
> 
I have tried running the scripts (running in terminal as well as just plain "Run") "makedrv", "wlan0up", and "wlan0dhcp" (in that order). I don't phsically see anything happening when I "Run" it. When I "Run in Terminal" and Terminal window pops up and saying a bunch of stuff then shuts down. I don't have time to read it.

Open the terminal from menu, go to the folder where the files are and run it by typing the name, f.e. "./makedrv". This should enable you to read what it says.

---

### Post by Powerman2442 on 2009-03-17
> **gtr32 said:**
> Open the terminal from menu, go to the folder where the files are and run it by typing the name, f.e. "./makedrv". This should enable you to read what it says.

Here is what it said...

derek@derek-desktop:~/Desktop/RTL8185_Linux_2.6_v1027.0823.2007/RTL8185_Linux_2.6_v1027.0823.2007$ ./makedrv
./ieee80211/
tar: ./ieee80211: Cannot mkdir: Permission denied
./ieee80211/ieee80211_module.c
tar: ./ieee80211/ieee80211_module.c: Cannot open: No such file or directory
./ieee80211/ieee80211_rx.c
tar: ./ieee80211/ieee80211_rx.c: Cannot open: No such file or directory
./ieee80211/tags
tar: ./ieee80211/tags: Cannot open: No such file or directory
./ieee80211/Makefile
tar: ./ieee80211/Makefile: Cannot open: No such file or directory
./ieee80211/ieee80211_crypt_tkip.c
tar: ./ieee80211/ieee80211_crypt_tkip.c: Cannot open: No such file or directory
./ieee80211/ieee80211_softmac.c
tar: ./ieee80211/ieee80211_softmac.c: Cannot open: No such file or directory
./ieee80211/readme
tar: ./ieee80211/readme: Cannot open: No such file or directory
./ieee80211/ieee80211_crypt_ccmp.c
tar: ./ieee80211/ieee80211_crypt_ccmp.c: Cannot open: No such file or directory
./ieee80211/ieee80211.h
tar: ./ieee80211/ieee80211.h: Cannot open: No such file or directory
./ieee80211/ieee80211_tx.c
tar: ./ieee80211/ieee80211_tx.c: Cannot open: No such file or directory
./ieee80211/ieee80211_softmac_wx.c
tar: ./ieee80211/ieee80211_softmac_wx.c: Cannot open: No such file or directory
./ieee80211/ieee80211_crypt.h
tar: ./ieee80211/ieee80211_crypt.h: Cannot open: No such file or directory
./ieee80211/ieee80211_wx.c
tar: ./ieee80211/ieee80211_wx.c: Cannot open: No such file or directory
./ieee80211/license
tar: ./ieee80211/license: Cannot open: No such file or directory
./ieee80211/ieee80211_crypt_wep.c
tar: ./ieee80211/ieee80211_crypt_wep.c: Cannot open: No such file or directory
./ieee80211/ieee80211_crypt.c
tar: ./ieee80211/ieee80211_crypt.c: Cannot open: No such file or directory
tar: Error exit delayed from previous errors
rtl8185/
tar: rtl8185: Cannot mkdir: Permission denied
rtl8185/README.adhoc
tar: rtl8185/README.adhoc: Cannot open: No such file or directory
rtl8185/r8180_sa2400.h
tar: rtl8185/r8180_sa2400.h: Cannot open: No such file or directory
rtl8185/Makefile
tar: rtl8185/Makefile: Cannot open: No such file or directory
rtl8185/copying
tar: rtl8185/copying: Cannot open: No such file or directory
rtl8185/README.master
tar: rtl8185/README.master: Cannot open: No such file or directory
rtl8185/r8180.h
tar: rtl8185/r8180.h: Cannot open: No such file or directory
rtl8185/install
tar: rtl8185/install: Cannot open: No such file or directory
rtl8185/r8180_max2820.h
tar: rtl8185/r8180_max2820.h: Cannot open: No such file or directory
rtl8185/r8180_max2820.c
tar: rtl8185/r8180_max2820.c: Cannot open: No such file or directory
rtl8185/r8180_rtl8225.h
tar: rtl8185/r8180_rtl8225.h: Cannot open: No such file or directory
rtl8185/r8180_wx.h
tar: rtl8185/r8180_wx.h: Cannot open: No such file or directory
rtl8185/authors
tar: rtl8185/authors: Cannot open: No such file or directory
rtl8185/tags
tar: rtl8185/tags: Cannot open: No such file or directory
rtl8185/r8180_pm.c
tar: rtl8185/r8180_pm.c: Cannot open: No such file or directory
rtl8185/r8180_hw.h
tar: rtl8185/r8180_hw.h: Cannot open: No such file or directory
rtl8185/r8180_gct.c
tar: rtl8185/r8180_gct.c: Cannot open: No such file or directory
rtl8185/r8180_gct.h
tar: rtl8185/r8180_gct.h: Cannot open: No such file or directory
rtl8185/r8180_rtl8225.c
tar: rtl8185/r8180_rtl8225.c: Cannot open: No such file or directory
rtl8185/readme
tar: rtl8185/readme: Cannot open: No such file or directory
rtl8185/r8180_93cx6.h
tar: rtl8185/r8180_93cx6.h: Cannot open: No such file or directory
rtl8185/ieee80211.h
tar: rtl8185/ieee80211.h: Cannot open: No such file or directory
rtl8185/license
tar: rtl8185/license: Cannot open: No such file or directory
rtl8185/r8180_pm.h
tar: rtl8185/r8180_pm.h: Cannot open: No such file or directory
rtl8185/changes
tar: rtl8185/changes: Cannot open: No such file or directory
rtl8185/r8180_rtl8225z2.c
tar: rtl8185/r8180_rtl8225z2.c: Cannot open: No such file or directory
rtl8185/r8180_wx.c
tar: rtl8185/r8180_wx.c: Cannot open: No such file or directory
rtl8185/r8180_rtl8255.c
tar: rtl8185/r8180_rtl8255.c: Cannot open: No such file or directory
rtl8185/r8180_93cx6.c
tar: rtl8185/r8180_93cx6.c: Cannot open: No such file or directory
rtl8185/r8180_sa2400.c
tar: rtl8185/r8180_sa2400.c: Cannot open: No such file or directory
rtl8185/r8180_core.c
tar: rtl8185/r8180_core.c: Cannot open: No such file or directory
rtl8185/r8180_rtl8255.h
tar: rtl8185/r8180_rtl8255.h: Cannot open: No such file or directory
rtl8185/ieee80211_crypt.h
tar: rtl8185/ieee80211_crypt.h: Cannot open: No such file or directory
tar: Error exit delayed from previous errors
./makedrv: line 5: cd: ieee80211: No such file or directory
make: *** No rule to make target `clean'.  Stop.
make: *** No targets specified and no makefile found.  Stop.
./makedrv: line 8: cd: ../rtl8185: No such file or directory
make: *** No rule to make target `clean'.  Stop.
make: *** No targets specified and no makefile found.  Stop.

Any clue?

---

### Post by gtr32 on 2009-03-17
> **Powerman2442 said:**
> 
Any clue?

Who owns the directory you are trying to execute the script from? Try 'sudo ./makedrv' instead to see if that helps.

---

### Post by Powerman2442 on 2009-03-17
> **gtr32 said:**
> Who owns the directory you are trying to execute the script from? Try 'sudo ./makedrv' instead to see if that helps.

I am the only user on this computer. I will try sudo.

---

### Post by chili555 on 2009-03-17
> Not exactly sure what that is. The Intrepid part leads me to believe that it is something that comes with 8.10.Is that not what you are running?

---

### Post by lvleph on 2009-03-17
RTL8185 Should work out of box. If it isn't then you should use ndiswrapper and the win98/me driver. This is the easiest way to get that card to work. I just got it working for my wife a couple days ago. Her's worked out of box, but was having strength issues. I installed the win98 driver and it works perfectly now.

---

### Post by Powerman2442 on 2009-03-17
> **chili555 said:**
> Is that not what you are running?

Nope, 8.04 aka. Hardy Heron. :D

---

### Post by chili555 on 2009-03-17
If the wired connection is working, open a terminal and do:```
sudo apt-get install linux-backports-modules-`uname -r`
```Those tick marks are on the keyboard with ~.

---

### Post by Powerman2442 on 2009-03-17
> **lvleph said:**
> RTL8185 Should work out of box. If it isn't then you should use ndiswrapper and the win98/me driver. This is the easiest way to get that card to work. I just got it working for my wife a couple days ago. Her's worked out of box, but was having strength issues. I installed the win98 driver and it works perfectly now.

Is that on 8.04 though? Or 8.10? I have 8.04 because I had problems with 8.10 on my computer.

---

### Post by Powerman2442 on 2009-03-17
> **chili555 said:**
> If the wired connection is working, open a terminal and do:```
sudo apt-get install linux-backports-modules-`uname -r`
```Those tick marks are on the keyboard with ~.

Would installing 8.10 help any? I had problems with it before, but I recently upgraded this computer so it might run better now. I got Xubuntu 8.10 that I might try right now. If that doesn't still run decently I will revert back to 8.04 and try that command with a wired connection.

Thanks,

Edit: Tried running Xubuntu 8.10 and it does the same thing every time. A blinking white underscore in the top left hand corner. Guess I will try the wired connection and run that command.

---

### Post by Powerman2442 on 2009-03-20
Typed "lspci -v | less" and it is detecting my wireless card. No way to set up setting for it anywhere. When I try typing in "sudo ./makedrv" it does a whole bunch of junk. Then I type "sudo ./wlan0up", like the install readme says, and it gives me a list of "No such file or folder." Wiped Ubuntu 8.04 off and tried about 8 different distros and none of them let me easily connect to the net. Either before or after I try installing this "driver" they gave me. I've read on a bunch of websites that Realtek 8185 works out-of-the-box. Not sure what box their getting their parts from. :S Anyone got any ideas? For right now I have no Ethernet card in this old PC. Only the dial-up modem and the wireless NIC. Need to buy a new Ethernet card or pull one from another PC and get connected and download ndiswrapper.

---

