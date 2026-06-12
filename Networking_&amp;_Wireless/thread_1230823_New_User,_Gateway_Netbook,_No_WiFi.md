---
title: "New User, Gateway Netbook, No WiFi"
date: 2009-08-03
forum: Networking &amp; Wireless
---

### Post by brhokla on 2009-08-03
Hi,  I'm new to using ubuntu and I installed the 9.04 64bit version on my little netbook.  It has 2 gigs ram, WiFi, and all works fin in Windows Vista but when I log into Ubuntu my Wifi doesn't light up at all.  It's as if it doesn't have WiFi and I'm completely new to Linux.  I will say everything else is working great.  Can anybody help me.  I can't even detect my wireless network as it's like the computer doesn't even have Wifi on it.  THANKS

---

### Post by philcamlin on 2009-08-03
please post output of 
iwconfig

---

### Post by brhokla on 2009-08-03
Logged in and started Terminal.

did iwconfig and it states the following:

lo          no wireless extensions.

eth0      no wireless extensions.

pan0     no wireless extensions.

---

### Post by lvleph on 2009-08-03
in terminal type ```
lspci
```

---

### Post by brhokla on 2009-08-03
brhoward@ubuntu:~$ lspci  
 00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge  
 00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)  
 00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)  
 00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)  
 00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA  
 00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)  
 00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)  
 00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)  
 00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)  
 00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)  
 00:14.1 IDE interface: ATI Technologies Inc SB600 IDE  
 00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)  
 00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge  
 00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge  
 00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration  
 00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map  
 00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller  
 00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control  
 01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]  
 03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)  
 04:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

---

### Post by lvleph on 2009-08-03
[Here you go.](http://ubuntuforums.org/showthread.php?p=7409939)

EDIT: This is the solution from that thread:
```
sudo apt-get install linux-backports-modules-jaunty
```

---

### Post by brhokla on 2009-08-03
Did the command 
sudo apt-get install linux-backports-modules-jaunty

came back and said E:  Couldn't find package linux-backports-modules-jaunty

---

### Post by lvleph on 2009-08-03
Open System>Administration>Software Sources and then check off all the boxes. Close and open terminal and type
```
sudo apt-get update
sudo apt-get install linux-backports-modules-jaunty
```

If that doesn't work try searching for it in Synaptic.

EDIT: Actually you will need to open the updates tab in Sources and check off the backports option.

---

### Post by brhokla on 2009-08-03
none of this worked but maybe it will once I hard wire this thing into the network.  I will try that.  Thanks for all the help.

---

### Post by lvleph on 2009-08-03
Sorry, I thought you were wired. You will need a network connection for sure.

---

### Post by brhokla on 2009-08-04
Well,  went and got a RJ-45 cable to connect computer to network but that won't work either.  Any ideas?

---

### Post by lvleph on 2009-08-04
I would put the Ubuntu CD in and install ndiswrapper. Once that is installed, get a hold of the XP driver for your card and use ndiswrapper to install it.

---

### Post by lvleph on 2009-08-04
Better yet download the backports deb.
[32 bit](https://launchpad.net/ubuntu/jaunty/i386/linux-backports-modules-jaunty-generic/2.6.28.13.17)
[64 bit](https://launchpad.net/ubuntu/jaunty/amd64/linux-backports-modules-jaunty-generic/2.6.28.11.15)

EDIT: Make sure you download the dependency and install that first.

---

### Post by Yanatsu on 2009-08-04
Okay, I'm just wondering about this, but 64 bit on a netbook? Try installing 32 bit Ubuntu, who knows, might solve it. And you've got 2GB RAM, you don't really need 64-bit, unless you're a performance junkie.

---

### Post by Mahler122 on 2009-08-04
This fix worked perfectly for me, Thanks!

---

### Post by brhokla on 2009-08-04
I'm going to try this and will update soon.  Thanks

---

### Post by MadHatter21 on 2009-08-04
Hey you need the ath9k driver for the atheros card. Go to (Rplace the xx with tt) hxxp://linuxwireless.org/en/users/Download and download the compat-wireless-2.6.30 and run 

make
sudo make install
sudo make unload

see how that works and get back to me. It should install the necessary driver for your card.

---

### Post by brhokla on 2009-08-04
I downloaded [linux-backports-modules-jaunty-generic_2.6.28.11.15_amd64.deb]("http://launchpadlibrarian.net/25578046/linux-backports-modules-jaunty-generic_2.6.28.11.15_amd64.deb")             (3.4 KiB)and then tried installing it on ubuntu and it says wrong architecture even though I'm using an AMD 64 and have the 64 bit version of ubuntu.

---

### Post by MadHatter21 on 2009-08-04
> **MadHatter21 said:**
> Hey you need the ath9k driver for the atheros card. Go to (Rplace the xx with tt) hxxp://linuxwireless.org/en/users/Download and download the compat-wireless-2.6.30 and run 

make
sudo make install
sudo make unload

see how that works and get back to me. It should install the necessary driver for your card.

Try this, literally you have the same set up as me. For all atheros ar***** cards the ath9k driver works.

---

### Post by brhokla on 2009-08-05
I think I'm going to have to take this to a pro.  I'm over my head with this but thought I would try it anyhow.

---

### Post by Yanatsu on 2009-08-05
Again, did you do what I said and try 32-bit Ubuntu? A 64-bit OS isn't suited for a Netbook...
Try that before you waste money.

---

### Post by brhokla on 2009-08-08
Just finally got more time to mess with this.  Haven't solved the problem yet but I will work on this tonight.  Any help would be appreciated.  I know nothing about Linux but so far playing with it on this little computer has been fun.  If I could only get the wifi to all work then I'd dump my Vista.

---

### Post by gmalivuk on 2009-08-09
> **MadHatter21 said:**
> Try this, literally you have the same set up as me. For all atheros ar***** cards the ath9k driver works.
I'm trying this at the moment (and logged in on my other computer).

Now, how would I do it if I didn't want to install all the other drivers beyond the one I'm actually interested in?

---

### Post by brhokla on 2009-08-10
I tried some stuff.  Read below!!!

	 	 brhoward@ubuntu:~$ modprobe ath9k  
 WARNING: Error inserting cfg80211 (/lib/modules/2.6.28-11-generic/kernel/net/wireless/cfg80211.ko): Operation not permitted  
 WARNING: Error inserting mac80211 (/lib/modules/2.6.28-11-generic/kernel/net/mac80211/mac80211.ko): Operation not permitted  
 FATAL: Error inserting ath9k (/lib/modules/2.6.28-11-generic/kernel/drivers/net/wireless/ath9k/ath9k.ko): Operation not permitted  
 brhoward@ubuntu:~$  
 

It say's operation not permitted on everything and I can't figure out why.  Any solutions?

Thanks

---

### Post by lvleph on 2009-08-10
You have to use sudo.

```
sudo modprobe ath9k
```

---

### Post by brhokla on 2009-08-10
Here is the latest:

	 	 brhoward@ubuntu:~$ lsmod|grep ath9k  
 ath9k                 263224  0  
 mac80211              217208  1 ath9k  
 led_class              12036  1 ath9k  
 brhoward@ubuntu:~$  
 
And 

	 	 brhoward@ubuntu:~$ iwconfig  
 lo        no wireless extensions.  
 

 pan0      no wireless extensions. 



I'm stumped.  it looks like the module is installed and shows me ath9k 263224 0 an so forth but I have no wireless.  Any ideas?

---

### Post by PhishShticks on 2010-03-14
I'm having this same issue on 9.10 should I perform the same steps?

---

### Post by randomsusers on 2011-06-10
I'm having a similar problem using the AR5001 card on an HP DV7-1451nr on Lucid Lynx. I'm searching websites looking for an answer and trying the things I see, but haven't had any luck. I've switched to 32 bit, loaded backports, and so on.

I notice a lot of threads just stop without another word and no indication of any solution found. Could someone who know post some closure? i.e. This was fix at [URL], or This will never be fixed, or its being works, see [URL] or something? I'd appreciate knowing if I'm wasting my time or not.

Thanks!

---

