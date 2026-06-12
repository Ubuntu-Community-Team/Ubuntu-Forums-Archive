---
title: "Wireless not working on Revo R3600"
date: 2010-04-30
forum: Networking &amp; Wireless
---

### Post by st0kes on 2010-04-30
I seem to be the only person with wireless problems on Ubuntu on the Revo3600 ... it contains an Atheros wlan card which simply not detected by Ubuntu (I'm using Xubuntu) ... are there any tips on getting this installed -- and unbreaking the broken state I have got my modules in :)

My system info - Ubuntu Lucid

```
lspci -v
05:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
        Subsystem: Foxconn International, Inc. Device e008
        Flags: bus master, fast devsel, latency 0, IRQ 9
        Memory at febf0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: [40] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [60] Express Legacy Endpoint, MSI 00
        Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
        Capabilities: [100] Advanced Error Reporting <?>
        Capabilities: [140] Virtual Channel <?>
        Kernel modules: ath5k
```

kernel version

```
uname -ra
Linux tinytron 2.6.32-21-generic-pae #32-Ubuntu SMP Fri Apr 16 09:39:35 UTC 2010 i686 GNU/Linux
```

iwconfig

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```

kernel modules ....

```
root@tinytron:~# lsmod | grep ath
ath                     7977  0
cfg80211              145185  2 mac80211,ath
root@tinytron:~# modprobe ath5k
FATAL: Error inserting ath5k (/lib/modules/2.6.32-21-generic-pae/updates/cw/ath5k.ko): Unknown symbol in module, or unknown parameter

```
I think it is failing to insert because of some earlier efforts to compile the ath5k/9k driver manually which have failed, I am not sure where to go from here. 

```
dmesg | tail
[58030.218890] ath5k: disagrees about version of symbol ieee80211_stop_queues
[58030.218897] ath5k: Unknown symbol ieee80211_stop_queues
[58030.219237] ath5k: disagrees about version of symbol ieee80211_unregister_hw
[58030.219242] ath5k: Unknown symbol ieee80211_unregister_hw
[58030.219470] ath5k: disagrees about version of symbol ath_regd_init
[58030.219474] ath5k: Unknown symbol ath_regd_init
[58030.219729] ath5k: disagrees about version of symbol ieee80211_beacon_get_tim
[58030.219734] ath5k: Unknown symbol ieee80211_beacon_get_tim
[58030.221608] ath5k: disagrees about version of symbol ieee80211_rts_duration
[58030.221620] ath5k: Unknown symbol ieee80211_rts_duration

```

Can anyone give me some hints for this driver? I don't mind using ndiswrapper if it gives me the wireless-n, otherwise I would like the native Linux driver to work.....

I think the modules wont load because it was compiled against an older kernel, but how can I delete this module now?

---

### Post by st0kes on 2010-05-02
Bump ... 

Can anyone help?

---

### Post by MatrixCat on 2010-05-02
I just finished getting my Wifi working on the Revo R3610.  I spent a solid week on and off so I'll save you the trouble.  Forget the built in drivers, forget madwifi (even the HAL drivers) and go straight to ndiswrapper.  The other driver did work for me, but not in any way I'd consider them 'working' - pings oscilating from 50ms up to 30000ms and constant dropouts made the net unusable.

There are very good instructions on the [Ubuntu Community Documentation]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")  They point you to where to check if ndiswrapper supports your WiFi card.  [My Atheros AR5001]("http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Atheros_AR5001") even had the link to the Windows drivers.  You might want to do a 'make uninstall' from the directories where you tried to compile drivers.  Hope that helps, cause I know how frustrating it was for me looking at a dozen entries [like this]("http://ubuntuforums.org/showthread.php?t=1378485&highlight=Revo") and getting nowhere.

---

### Post by st0kes on 2010-05-03
I really appreciate your reply. I had already spent about 4 hours trying various drivers and troubleshooting make and gcc problems before posing my questions here!
 

One question for you though before I go down the ndiswrapper route. Did the Windows driver enable wireless-n on your card? Because if not I'll just go and buy a long network cable ... I want to do video streaming with this computer and wiress-g just ain't gonna cut it. :)

---

### Post by MatrixCat on 2010-05-03
Um, actually I'm afraid I have no way to check as the router I connect to is only 802.11g.  I get the full 54MBps, but if you're going to shift lots of data cable is the way to go.  Good luck!

---

### Post by gordintoronto on 2010-05-03
> **st0kes said:**
> Did the Windows driver enable wireless-n on your card? Because if not I'll just go and buy a long network cable ... I want to do video streaming with this computer and wiress-g just ain't gonna cut it. :)

Unless you have very high resolution videos (blu-ray), wireless G is more than adequate.

---

### Post by st0kes on 2010-05-04
It is just wireless-g. I'll ditch this and either use a long cat 5 cable or a wireless-n adapter (woich could be more fun)

Sadly wireless-g is not an option for me, there are too many other 'g' networks around me which cause the signal from my router to be too unreliable for anything like video streaming ...

---

### Post by Anthem on 2010-05-17
Hey guys, this is a simple bug in the Lucid stock install.  It's easily fixable with no extra driver installation.  Simply do this as root:

```
mkdir -p /etc/Wireless/RT2860STA/
touch /etc/Wireless/RT2860STA/RT2860STA.dat
service network-manager restart
```

Done.  Have a nice day!

---

EDIT:  Those interested can find a full discussion here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620)

I know the title says it's about the RT3090 driver, but the Revo 3600 has the RT2860STA chipset and this solved it for me.

---

### Post by mazadillon on 2010-08-22
> **Anthem said:**
> Hey guys, this is a simple bug in the Lucid stock install.  It's easily fixable with no extra driver installation.  Simply do this as root:

```
mkdir -p /etc/Wireless/RT2860STA/
touch /etc/Wireless/RT2860STA/RT2860STA.dat
service network-manager restart
```

Done.  Have a nice day!


Thanks, the wifi appeared to all be working except it wouldn't detect any access points, this simple fix worked instantly, thanks :)

---

### Post by declan23 on 2010-12-15
hi. this may or may not be directly relevant but I had an issue establishing a wifi connection between my revo atom pc which has an atheros card. my access point is linksys wrtg54. I could see the access point and signal strength was good but always failed to connect. Having installed the madwifi drivers and rebooted still had the issue. (I am using ubuntu 10). What fixed it was to change the wep key setting on my router from "shared" to Auto and it worked. (I had also tried changing the wifi channel a few times on the router but it was the wep key setting that solved the issue.

---

