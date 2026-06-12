---
title: "Artheros ar5211 [168c:002c] (rev 01)"
date: 2009-12-31
forum: Networking &amp; Wireless
---

### Post by chrisrulesall on 2009-12-31
It seems that this particular wireless card is not supported (the 002c) I got a D1130 Avaretec and put ubuntu 9.10 on there. 

01:00.0 Network controller [0280]: Atheros Communications Inc. Device [168c:002c] (rev 01)
    Subsystem: Device [1a3b:1112]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 10
    Region 0: Memory at fe9f0000 (64-bit, non-prefetchable) [size=64K]


After much googling, i only found things for 168c:001c

maybe 002c is a new revision? i dont know how those id's work persay

I tried the ath5k driver, and the hardware is not found by the driver, lshw shows UNASSIGNED or whatever it says. (UN-something).

same thing with the madwifi driver, and the madwifi driver compiled from trunk.

I also tried the ndiswrapper route, and loaded the driver for xp from their website (which is the ar5211 driver)(from here [http://www.trigem.com/us/support/drivers.asp?cate_seq=1&subcate_seq=33&product_seq=84](http://www.trigem.com/us/support/drivers.asp?cate_seq=1&subcate_seq=33&product_seq=84)), and the same thing, the hardware is not detected to be initiated. 

the modules would simply load without errors, but also without finding the hardware. 

Out of curiousity i peaked in /etc/ndiswrapper/net5211 and noticed that there were many conf files for many versions and id's except for :002c. So for a shot in the dark i copied a similar conf file to 168C:002C:1112:1A3B.5.conf
modprobe'd ndiswrapper, and ndiswrapper tried to load the device, but failed with an error. Unfortunatly i dont have the exact error at this very moment on hand. But it was 1 step closer.

I would much rather get madwifi or ath5k driver working over ndiswrapper, but if i must settle for ndiswrapper, then ok.

If anyone can provide any help on getting this to work, please send me a line, ive been beating my head on the door all day now, and have a very short deadline.

---

### Post by chrisrulesall on 2010-01-01
ok got some new info. I think the driver download from the website is wrong. the device is apparently an ar2427.

---

### Post by karako on 2010-01-04
> **chrisrulesall said:**
> ok got some new info. I think the driver download from the website is wrong. the device is apparently an ar2427.


I think I am having the same wifi chipset, reported by the system as [168c:002c], in my new netbook with Ubuntu 9.10 installed by myself.

I managed to get the Wifi working with NDISWRAPPER and Windows driver came with the netbook, feel free to try the attachment.

However, I had unloaded the NDISWRAPPER and moved on to Madwifi, because I want to run Spoonwep under Ubuntu.  Unfortunately, the Madwifi driver didn't work.  It can't even recognize the hardware.

---

### Post by isidoro on 2010-01-12
> **karako said:**
> I think I am having the same wifi chipset, reported by the system as [168c:002c], in my new netbook with Ubuntu 9.10 installed by myself.

I managed to get the Wifi working with NDISWRAPPER and Windows driver came with the netbook, feel free to try the attachment.

However, I had unloaded the NDISWRAPPER and moved on to Madwifi, because I want to run Spoonwep under Ubuntu.  Unfortunately, the Madwifi driver didn't work.  It can't even recognize the hardware.
Thanks!!
Ndiswrapper also worked in my ASUS Eee PC 1005P (with Atheros AR2427 chipset). But doesn't recognize the driver you posted, and I used this driver:
Atheros Wireless LAN Windows XP 7.7.0.329 WHQL

---

### Post by James Little on 2010-01-20
I also need to get this working and would prefer not to use ndiswrapper. I have the Asus 1005PE which uses AR2427 chipset. I compiled the ath5k ok, and can modprobe it without an error, but the device is simply not seen, nothing in ifconfig, nothing in iwconfig and as far as I can tell, nothing pertaining to the wifi chip in dmesg after boot. ath5k is not blacklisted. 

Any help greatly appreciated.

---

### Post by gregpritchard on 2010-01-21
isidoro - you're my new hero. I've beating my head against the desk for three days trying to get this thing working. That's just nailed it!

Asus 1005P, Ubuntu Netbook Remix 9.10 (Karmic)

Is Happy. Is Good.

---

### Post by DangeR MaN on 2010-04-08
I have eee pc 1005p. But i can't install any driver (ndisgtk).
"Driver is wrong!" Help me please:popcorn:

---

### Post by khunter1 on 2010-04-08
> **DangeR MaN said:**
> I have eee pc 1005p. But i can't install any driver (ndisgtk).
"Driver is wrong!" Help me please:popcorn:

Try this file netathw.inf with ndisgtk:

[http://www.mediafire.com/?wok4kdkm1q5](http://www.mediafire.com/?wok4kdkm1q5)

Also post here:

[https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.32/+bug/521967](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.32/+bug/521967)

---

### Post by dionblundell on 2010-04-18
This is a way of getting your wireless to work.

It is better than using the windows drivers:
1) better link quailty
2) GNU linux module, rather than windows
3) easy

Go here:
[http://wireless.kernel.org/download/compat-wireless-2.6/](http://wireless.kernel.org/download/compat-wireless-2.6/)
and download the latest drivers, for example:
[]("http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-04-16.tar.bz2")[http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-04-18.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-04-18.tar.bz2)

Now extract these files
Open a SHELL, and change into the directory created with the archive,   it's probably something like:
```
cd ~/Downloads/compat-wireless-2010-04-18

```now select the driver
```
./scripts/driver-select ath9k
```You now need to build the   drivers
```
make
```Now install them with this
```
sudo make install
sudo make unload
sudo modprobe ath9k
```You will need to do ALL the above EACH TIME the kernel is   updated.
Networking works perfectly for me on my ASUS 1005PE now

---

### Post by khunter1 on 2010-04-27
@dionblundell:

Followed all your steps. The last one = Errors

                 ```
asus@Asus:~/Downloads/compat-wireless-2010-04-26$  sudo modprobe ath9k
 WARNING: Error inserting ath9k_hw (/lib/modules/2.6.31-20-generic/updates/drivers/net/wireless/ath/ath9k/ath9k_hw.ko):  Unknown symbol in module, or unknown parameter (see dmesg)
 WARNING: Error inserting ath9k_common (/lib/modules/2.6.31-20-generic/updates/drivers/net/wireless/ath/ath9k/ath9k_common.ko):  Unknown symbol in module, or unknown parameter (see dmesg)
 WARNING: Error inserting mac80211 (/lib/modules/2.6.31-20-generic/updates/cw/mac80211.ko):  Unknown symbol in module, or unknown parameter (see dmesg)
 FATAL: Error inserting ath9k (/lib/modules/2.6.31-20-generic/updates/drivers/net/wireless/ath/ath9k/ath9k.ko):  Unknown symbol in module, or unknown parameter (see dmesg)
 asus@Asus:~/Downloads/compat-wireless-2010-04-26$

```

---

### Post by dionblundell on 2010-04-28
see my reply here:
[http://ubuntuforums.org/showthread.php?t=1396854&page=3](http://ubuntuforums.org/showthread.php?t=1396854&page=3)
rather than cross-posting...

---

### Post by isidoro on 2010-05-03
> **dionblundell said:**
> This is a way of getting your wireless to work.
...
THANKS!! Works better than ndiswrapper in my 1005P.
With ndiswrapper I had a lot of problems, but this WORKS PERFECTLY!!

---

### Post by bobandiara on 2010-05-30
Hello! I have the same wireless card on my notebook, a Sim+ model made by the brazilian manufacturer Positivo on which I installed Ubuntu 10.04. I tried this method to access my wireless router at home and it worked at the first attempt!

Thank you very much for sharing this!

---

### Post by prytoluk on 2010-07-12
> **bobandiara said:**
> Hello! I have the same wireless card on my notebook, a Sim+ model made by the brazilian manufacturer Positivo on which I installed Ubuntu 10.04. I tried this method to access my wireless router at home and it worked at the first attempt!

Thank you very much for sharing this!
Exactly the same thing for me, same pc, same OS, lol.
Thank you very much dude!

---

