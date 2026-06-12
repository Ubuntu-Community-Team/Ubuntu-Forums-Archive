---
title: "Broadcom 43xx logging into secure network"
date: 2009-04-09
forum: Networking &amp; Wireless
---

### Post by pruggles on 2009-04-09
I just upgraded to Ibex, and I have not been able to log into a secure wifi network, unsecure are just fine.  When I was on Hardy a switch of driver for my 4312 Broadcom (rev.1) card seemed to work, so I tried that again.  Well, I followed the directions at [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff]("http://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff").  I read through it, and it said that the directions would apply to Intrepid as well even though the post was written way back in feisty.

In the first place, when I looked for the chipset (lspci -n | grep '14e4:43') the result-- 14e4:4315 (rev 01), which the chart associated with a BCM 4310 (rev 01)-- did not match the result of lspci | grep Broadcom-- BCM 4312 (rev 01).

Like a fool I followed the directions for the chipset and then, when that didn't work, the driver.  Now, I have to manually turn on my driver through Sytem--Administration--Hardware/Drivers, and I still cannot log into secure networks.

Ideas?

---

### Post by kevdog on 2009-04-09
Wont the b43 driver work for you?

---

### Post by pruggles on 2009-04-09
Right after I submitted I thought I should add, I'm running a Dell Vostro 1000 with a AMD 64 architecture.

---

### Post by pruggles on 2009-04-09
Kevdogg, It's possible that it would work.  I'm new so say more.

---

### Post by Ayuthia on 2009-04-09
Can you post the results of lshw -C network?  It could be possible that the wl module is interfering with ndiswrapper.  Have you tried the following:
```
sudo modprobe -r b43 ssb wl ndiswrapper
sudo modprobe ndiswrapper
sudo ifconfig wlan0 up
sudo iwlist scan
```
This will remove the possible wireless modules and load ndiswrapper.  

If your card is a 14e4:4315 card, you will not be able to use the b43 module yet.  They just finished up the reverse-engineering (or almost completed) for it so they will need to most likely create the specifications and then develop the code for it.

You should be able to use the Broadcom STA module (wl) or ndiswrapper.  The Broadcom STA module has a lot of problems with WEP/WPA.  Most likely you will need to compile the most recent STA module with the WPA patch to make it work.  Here is the link to the site:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
You can try this [guide]("http://linuxfans.betaserver.org/index.php?option=com_content&view=article&id=48:guide-to-compiling-and-using-the-broadcom-sta-module&catid=34:guides&Itemid=61") to install it.  The only thing that you will need to do is replace step 5 with this patch:
[http://www.broadcom.com/docs/linux_sta/wl_iw_v2.patch](http://www.broadcom.com/docs/linux_sta/wl_iw_v2.patch)
And patch it by:
```
patch -p1 < wl_iw_v2.patch
```

You might want to try the ndiswrapper method first to see if you can get it to work.  If it does not work you can then try the compiling version since it is not quite a good start for a person learning Linux.

---

### Post by pruggles on 2009-04-09
The Result of lshw -C network is
 
*-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 01
       serial: 00:22:5f:1b:8e:73
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl1 driverversion=5.10.27.12 ip=192.168.1.102 latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:78:4e:a0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 7a:84:c5:41:06:1d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

give me a moment to try the commands you suggested.

---

### Post by pruggles on 2009-04-09
sudo modprobe -r b43 ssb wl ndiswrapper results in "fatal ssb in use."

---

### Post by Ayuthia on 2009-04-09
> **pruggles said:**
> sudo modprobe -r b43 ssb wl ndiswrapper results in "fatal ssb in use."

You have a Broadcom wired ethernet card!  Ok.  It just means that you will need a workaround to get the cards to work.  Try the following:
```
sudo modprobe -r b43 b44 ssb ndiswrapper wl
sudo modprobe ndiswrapper
sudo modprobe b44
sudo ifconfig eth0 up
sudo ifconfig wlan0 up
sudo iwlist scan
```

If that doesn't work, we might try the wl option without compiling.  It might be possible that the wl module was not able to run properly because it was loaded after the ssb module (which is a problem).

---

### Post by pruggles on 2009-04-09
Still no dice,


Here are the results of the last batch of commands:

ifconfig wlan0 up
wlan0: ERROR while getting interface: No such device
iwlist scan
lo      Interface doesn't support scanning
pan0    Interface doesn't support scanning
eth0    Interface doesn't support scanning
eth1    Interface doesn't support scanning

I've gotten that response from the 'iwlist scan' command before.

What's the wl option without compiling?

---

### Post by pruggles on 2009-04-09
bump

---

### Post by Ayuthia on 2009-04-09
```
sudo modprobe -r b43 b44 ssb ndiswrapper wl
sudo modprobe wl
sudo modprobe b44
sudo /etc/init.d/networking restart
sudo iwlist scan
```
I am re-reading your original message.  Have you been able to connect to unsecured websites?  If so, then most likely it is the wl module that is not working.  From there you might need to go the compiled route.

---

### Post by pruggles on 2009-04-10
bump

---

### Post by pruggles on 2009-04-13
> **Ayuthia said:**
> 

You should be able to use the Broadcom STA module (wl) or ndiswrapper.  The Broadcom STA module has a lot of problems with WEP/WPA.  Most likely you will need to compile the most recent STA module with the WPA patch to make it work.  Here is the link to the site:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
You can try this [guide]("http://linuxfans.betaserver.org/index.php?option=com_content&view=article&id=48:guide-to-compiling-and-using-the-broadcom-sta-module&catid=34:guides&Itemid=61") to install it.  The only thing that you will need to do is replace step 5 with this patch:
[http://www.broadcom.com/docs/linux_sta/wl_iw_v2.patch](http://www.broadcom.com/docs/linux_sta/wl_iw_v2.patch)
And patch it by:
```
patch -p1 < wl_iw_v2.patch
```

You might want to try the ndiswrapper method first to see if you can get it to work.  If it does not work you can then try the compiling version since it is not quite a good start for a person learning Linux.

Yes, I can get on non-secure networks.  Also, for the life of me, I can't finish the directions in [guide]("http://linuxfans.betaserver.org/index.php?option=com_content&view=article&id=48:guide-to-compiling-and-using-the-broadcom-sta-module&catid=34:guides&Itemid=61") because I can't remove the ssb module.  It always says that it's in use, even after I tried to black list it.

---

### Post by pruggles on 2009-04-13
> **Ayuthia said:**
> 

You should be able to use the Broadcom STA module (wl) or ndiswrapper.  The Broadcom STA module has a lot of problems with WEP/WPA.  Most likely you will need to compile the most recent STA module with the WPA patch to make it work.  Here is the link to the site:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
You can try this [guide]("http://linuxfans.betaserver.org/index.php?option=com_content&view=article&id=48:guide-to-compiling-and-using-the-broadcom-sta-module&catid=34:guides&Itemid=61") to install it.  The only thing that you will need to do is replace step 5 with this patch:
[http://www.broadcom.com/docs/linux_sta/wl_iw_v2.patch](http://www.broadcom.com/docs/linux_sta/wl_iw_v2.patch)
And patch it by:
```
patch -p1 < wl_iw_v2.patch
```

You might want to try the ndiswrapper method first to see if you can get it to work.  If it does not work you can then try the compiling version since it is not quite a good start for a person learning Linux.

Yes, I can get on non-secure networks.  Also, for the life of me, I can't finish the directions in [guide]("http://linuxfans.betaserver.org/index.php?option=com_content&view=article&id=48:guide-to-compiling-and-using-the-broadcom-sta-module&catid=34:guides&Itemid=61") because I can't remove the ssb module.  It always says that it's in use, even after I tried to blacklist it.

---

### Post by Ayuthia on 2009-04-13
> **pruggles said:**
> Yes, I can get on non-secure networks.  Also, for the life of me, I can't finish the directions in [guide]("http://linuxfans.betaserver.org/index.php?option=com_content&view=article&id=48:guide-to-compiling-and-using-the-broadcom-sta-module&catid=34:guides&Itemid=61") because I can't remove the ssb module.  It always says that it's in use, even after I tried to blacklist it.

This is because you have a b44 module (wired ethernet card) that needs ssb.  You will need to add the following workaround to load the wl module before b44 and ssb:
```
echo -e '#ssb workaround, added `date`\ninstall wl modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install wl $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/wl
```

---

### Post by pruggles on 2009-04-13
> **Ayuthia said:**
> This is because you have a b44 module (wired ethernet card) that needs ssb.  You will need to add the following workaround to load the wl module before b44 and ssb:
```
echo -e '#ssb workaround, added `date`\ninstall wl modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install wl $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/wl
```

Ayuthia, have I thanked you yet for sticking with me on this?  You've really been awesome.

Anyway, I'm not quite there yet.  I ran your workaround, and ssb is still running (even after restarting).  Also, I don't know if this means anything, but I've got a module redundancy.  While looking though the computer to see where these things actually are (while not touching them through the GUI) I noticed that I had a batch of modules for the 2.6.27-11 kernel and another batch for the 2.6.27-7 kernel.  Everything between them seems to be pretty identical.  Is it possible that the redundancy is screwing up the process?  When I check my kernel version on the terminal I'm running 2.6.27-11, and I don't know when the mods for 2.6.26-7 got into the system.

---

### Post by Ayuthia on 2009-04-13
> **pruggles said:**
> Ayuthia, have I thanked you yet for sticking with me on this?  You've really been awesome.

Anyway, I'm not quite there yet.  I ran your workaround, and ssb is still running (even after restarting).  Also, I don't know if this means anything, but I've got a module redundancy.  While looking though the computer to see where these things actually are (while not touching them through the GUI) I noticed that I had a batch of modules for the 2.6.27-11 kernel and another batch for the 2.6.27-7 kernel.  Everything between them seems to be pretty identical.  Is it possible that the redundancy is screwing up the process?  When I check my kernel version on the terminal I'm running 2.6.27-11, and I don't know when the mods for 2.6.26-7 got into the system.
Each kernel version has its own set of modules.  They are going to be pretty similar because there was an update to the 2.6.27 kernel.

As for the ssb module, you will still need to have it there.  If you type:
```
lsmod|grep ssb
```you should see that it is only attached to the b44 module.  The workaround script will remove the ssb module, load the wl module, then load the b44 and ssb modules back.

You should check to see if the wl module is loaded:
```
lsmod|grep wl
lshw -C network
```
Both results should show that the wl module is there and it is attached to the wireless card.  If you are able to see them, you should be able to see wireless sites:
```
sudo iwlist scan
```
If you are able to see wireless sites, we then need to figure out if the issue is with the driver or with NetworkManager.

---

### Post by pruggles on 2009-04-15
I ran those commands and I can see the workaround, and that the wl module is loaded, and the wireless networks.  I can get connected to non-secure networks. Here are the results

> 
Sudo iwlist scan

eth1      Scan completed :
          Cell 01 - Address: 00:06:25:25:9A:7C
                    ESSID:"LTSP1"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:4/5  Signal level:-61 dBm  Noise level:-18 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
          Cell 02 - Address: 00:12:17:6D:57:F1
                    ESSID:"LTSP1"
                    Mode:Managed
                    Frequency=2.437 GHz (Channel 6)
                    Quality:5/5  Signal level:-57 dBm  Noise level:-18 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s


>  lsmod | grep ssb
ssb                    46340  1 b44


> lsmod | grep wl
wl                   1089360  0 
ieee80211_crypt        14596  2 ieee80211_crypt_tkip,wl


>  sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 01
       serial: 00:22:5f:1b:8e:73
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.27.12 ip=10.0.2.18 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg

---

### Post by Ayuthia on 2009-04-15
```
sudo lshw -C network
*-network
description: Wireless interface
product: BCM4312 802.11b/g
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:05:00.0
logical name: eth1
version: 01
serial: 00:22:5f:1b:8e:73
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=wl0 driverversion=5.10.27.12 ip=10.0.2.18 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg 
```This shows that you are using the 5.10.27.12 version of the wl module.  I am assuming that this is the Ubuntu supplied version because the current version is higher.  Were you able to get the compiled one to compile successfully?

Are you trying to use WEP or WPA and also are you using NetworkManager (Ubuntu's default network manager), wicd, or something else to connect?  I know that the wl module and NetworkManager have been known to have problems in Ubuntu for WEP and WPA.

You might try this link to see if you can connect manually:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)
It is a guide on how to connect to wireless connections manually.

---

### Post by pruggles on 2009-04-17
The manual login worked, which is good enough so that I can get on to my home network.  So, it must be NetworkManager that's still being flaky.  I'll try to uninstall and reinstall; maybe that will work.  Otherwise, I might come back to this later, but I'm OK for now. 

Thanks for all your help. :D

---

