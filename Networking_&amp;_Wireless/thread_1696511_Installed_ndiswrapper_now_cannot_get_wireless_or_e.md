---
title: "Installed ndiswrapper now cannot get wireless or ethernet"
date: 2011-02-27
forum: Networking &amp; Wireless
---

### Post by d3nn on 2011-02-27
So I installed ndiswrapper and got it half working, but the driver was "invalid", then I installed ath9k_htc installer and I got the wireless, but then I rebooted and did not have a wireless or a wired connection, (which I did have, I was just trying to get wireless working too with my netgear wna1100 card)
 
So now I would be fine with just dealing with only wireless by fixing ath9k_htc or ndiswrapper or a wired connection.

---

### Post by walt.smith1960 on 2011-02-27
Rerun ath9k installer.  A kernel upgrade will break a compiled driver , rerunning the installer should fix it.

---

### Post by d3nn on 2011-02-27
I reinstalled ath9k but it didn't do anything.

---

### Post by walt.smith1960 on 2011-02-27
> **d3nn said:**
> I reinstalled ath9k but it didn't do anything.

Did the installer work before the latest download?  I've had happen what you had happen and running the installer again fixed it.  I see you had  failed partial install of NDISwrapper.  I wonder if some remnants from that are causing problems.  You did do a restart after running ath9k installer, yes?

---

### Post by d3nn on 2011-02-27
I did restart it, and i uninstalled everything I could of ndiswrapper from synaptic packet manager, but i suppose there could be something left of ndiskwrapper.

---

### Post by walt.smith1960 on 2011-02-28
Hmmm, I'm not sure what to tell you.  I did lose my Netgear WNA1100 this morning for a short time but a restart brought it back. I think plugging a USB drive may have caused the disconnect but I don't know how or why.  Here are the results of my dmesg if you'd like to compare mine to yours to check ath9k related stuff
```
[   11.588799] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   11.793158] ath: EEPROM regdomain: 0x60
[   11.793161] ath: EEPROM indicates we should expect a direct regpair map
[   11.793164] ath: Country alpha2 being used: 00
[   11.793166] ath: Regpair used: 0x60
[   11.801313] Registered led device: ath9k-phy0::radio
[   11.801332] Registered led device: ath9k-phy0::assoc
[   11.801343] Registered led device: ath9k-phy0::tx
[   11.801353] Registered led device: ath9k-phy0::rx
[   11.801355] usb 2-2: ath9k_htc: USB layer initialized
[   11.801374] usbcore: registered new interface driver ath9k_hif_usb
[   11.820426] udev[436]: renamed network interface wlan0 to wlan1
[   11.861550] ppdev: user-space parallel port driver
[   12.023028] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   12.890658] usb 1-3.1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[   14.536042] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   15.238762] wlan1: authenticate with 00:26:62:7c:b1:5b (try 1)
[   15.240897] wlan1: authenticated
[   15.240917] wlan1: associate with xx:xx:xx:xx:xx:xx (try 1)
[   15.244280] wlan1: RX AssocResp from xx:xx:xx:xx:xx:xx (capab=0x431 status=0 aid=2)
[   15.244283] wlan1: associated
[   15.311411] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[   15.311614] cfg80211: Calling CRDA for country: US
[   15.451419] Intel AES-NI instructions are not detected.
[   15.471560] padlock: VIA PadLock not detected.
[   25.860638] wlan1: no IPv6 routers present
everyday@secondfloordesktop:~$ 

```

---

### Post by d3nn on 2011-02-28
I can't figure out how to transfer what dmesg says from my no connection linux machine to my windows machine, but it says this after I plug it in without any mention of wlan0 or wlan1 though.
 
 
[ 11.801313] Registered led device: ath9k-phy0::radio
[ 11.801332] Registered led device: ath9k-phy0::assoc
[ 11.801343] Registered led device: ath9k-phy0::tx
[ 11.801353] Registered led device: ath9k-phy0::rx
[ 11.801355] usb 2-2: ath9k_htc: USB layer initialized
 
 
My iwconfig is this
 
 
lo no wireless extensions
 
eth0 no wireless extensions
 
 
wlan0 IEEE 802.11bgn ESSID: off/any
 
Mode: managed Access point: Not-associated 
 
 
then some other stuff that looks unimportant.
 
 
 
I'd really be more than happy to be able to just go back to my wired connection, but that stopped working along with my new wireless connection.

---

### Post by walt.smith1960 on 2011-02-28
> **d3nn said:**
> I can't figure out how to transfer what dmesg says from my no connection linux machine to my windows machine, but it says this after I plug it in without any mention of wlan0 or wlan1 though.
 
 
[ 11.801313] Registered led device: ath9k-phy0::radio
[ 11.801332] Registered led device: ath9k-phy0::assoc
[ 11.801343] Registered led device: ath9k-phy0::tx
[ 11.801353] Registered led device: ath9k-phy0::rx
[ 11.801355] usb 2-2: ath9k_htc: USB layer initialized
 
 
My iwconfig is this
 
 
lo no wireless extensions
 
eth0 no wireless extensions
 
 
wlan0 IEEE 802.11bgn ESSID: off/any
 
Mode: managed Access point: Not-associated 
 
 
then some other stuff that looks unimportant.
 
 
 
I'd really be more than happy to be able to just go back to my wired connection, **but that stopped working along with my new wireless connection**.

Hmmm, to lose both wired & wireless goes beyond your Netgear device not being recognized.  Have you tried right-clicking the network manager icon and making sure networking & wireless are enabled? I've had networking uncheck itself for no apparent reason which disables both wired & wireless.

---

### Post by d3nn on 2011-03-01
I know this sounds uber noobish, but where is the icon? I remember one being there, but i might have taken it off.

---

### Post by d3nn on 2011-03-01
Excuse me for saying this, but you are a stud. I simply searched for how to
Fix that applet and enabled networking, now it's workinglike a charm. Thanks so much!

---

