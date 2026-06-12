---
title: "Still problems w/ BC4312rev01"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by sanskaras on 2009-11-02
So my thread was closed in the karmic forum and I still can't figure my wireless problems out.

It stalls randomly for a couple seconds to a couple minutes with a TKIP error repeating in the log file.

I've only noticed this on WPA/WPA2 networks, works fine on unsecured networks (tested it today).

I'm tired of pissing with it so I thought maybe theres another driver I can use?  I'm currently using the wl restricted driver.

Is there another one I can try, or an old version of the wl driver?  I never had this problem in hardy and jaunty.  Just in intrepid and karmic, so maybe the driver has been updated since?

Or does anyone know where I can look to troubleshoot errors with TKIP?  Heres the message I get when it craps out - 
Oct 30 06:11:14 nick-laptop kernel: [ 9794.505985] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=f383db40

If I can't get this fixed I'm going to have to switch to a different distro :(  I need consistent internet.

Thanks!!

---

### Post by sanskaras on 2009-11-02
I checked the b43 driver site seems I have the 

0b:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

card to be exact and the are in progress in supporting it.  Guess that driver is out.

Hmmmm

---

### Post by endorphine44 on 2009-11-02
check this thread, seems we've all had some problems with wireless on 9.10. Some are able to get it working. I've not had any luck with my Dell 1395 (BC4312) card so far.
[http://ubuntuforums.org/showthread.php?t=1309760](http://ubuntuforums.org/showthread.php?t=1309760)

---

### Post by sanskaras on 2009-11-03
Thanks, I tried compiling the wl driver myself and installing it and it seems to be working great so far.  Won't know for sure for a day or so, sometimes I had streaks of good luck before though.  We'll see! (Oh, before this I also tried 64bit ubuntu and got the same exact symptoms, and I'm still running the 64bit).

Anyways, on a side note anyone know how make the wl driver load on boot?
Right now I have the wl.ko driver on my desktop and I have to run
sudo insmod /home/nick/Desktop/wl.ko to start the wireless up.

I think I would place the wl.ko driver in /lib/modules/2.6.31-14-generic/kernel/net/wireless, but then what else do I have to do?

Just place insmod /lib/modules/2.6.31-14-generic/kernel/net/wireless/wl.ko in some boot file??

Thanks!

---

### Post by sanskaras on 2009-11-03
Nvm it didn't work..

```
Nov  3 12:50:35 nick-laptop wpa_supplicant[1298]: WPA: Group rekeying completed with 00:1e:58:ed:38:61 [GTK=TKIP]
Nov  3 12:50:35 nick-laptop NetworkManager: <info>  (eth2): supplicant connection state:  completed -> group handshake
Nov  3 12:50:35 nick-laptop NetworkManager: <info>  (eth2): supplicant connection state:  group handshake -> completed
Nov  3 12:51:11 nick-laptop kernel: [ 3047.571843] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=ffff8801005b8240
Nov  3 12:51:12 nick-laptop kernel: [ 3048.637758] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=ffff8801005b8240
Nov  3 12:51:13 nick-laptop kernel: [ 3049.681728] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=ffff8801005b8240
Nov  3 12:51:14 nick-laptop kernel: [ 3050.705489] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=ffff8801005b8240
Nov  3 12:51:15 nick-laptop kernel: [ 3051.729495] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=ffff8801005b8240
Nov  3 12:51:16 nick-laptop kernel: [ 3052.756813] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=ffff8801005b8240
```

But I did notice this happens after something to do with group re-keying and group handshakes?  Anyone know what that means?

I reconnected after the rekying message and the TKIP errors stopped.  So apparently it's just a problem with the wpa rekeying er somthing after
that.

---

