---
title: "ath9k_htc limited to 1 Mbps"
date: 2010-09-18
forum: Networking &amp; Wireless
---

### Post by TVAbuntu on 2010-09-18
I have a new TP-link TL-WN721N usb adapter (picked up for essentially free) and wanted to try it out. It uses the ath9k_htc driver and ar9271 firmware. I downloaded compat-wireless as it isn't in the kernel until 2.6.35 and made as per instructions ([http://wireless.kernel.org/en/users/Download#Drivers]("http://wireless.kernel.org/en/users/Download#Drivers") for those who might be interested)
It works, but I'm only getting 1 Mbps, as opposed to my usual 54 (with DWA-140 using rt2870--wireless router is Asus WL-520GU running tomato so 54 Mbps is the limit). 
Anyone have this working at speed using the native driver and firmware?

---

### Post by walt.smith1960 on 2010-09-19
Just a thought--how do you know you're limited to 1 Mbps? I have an adapter that one says it's 1 Mbps but when I run a speedtest.net test, it comes out at 2.9 Mbps. Does the connection seem slow?  My system>administration>network tools>devices>wireless interfaces>wireless interfaces shows link speed of 1Mbps. Mine is considerably faster than that.

---

### Post by termin on 2010-09-19
go to the terminal and type:
sudo iwconfig wlan0(or wlan1) rate 54M
or if thats still slow than type:
sudo iwconfig wlan0(or wlan1) rate 11M


one of those has to work

---

### Post by TVAbuntu on 2010-09-20
How do I know:
> 
wlan2     IEEE 802.11bgn  ESSID:"xxxxxxxx"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:24:8C:00:A6:85   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=43/70  Signal level=-67 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Tried the easy fix:

> $ sudo iwconfig wlan2 rate 54M
Error for wireless request "Set Bit Rate" (8B20) :
    SET failed on device wlan2 ; Operation not supported.

same result for 11M.

---

### Post by shearerc on 2011-02-08
Same issue here (TN-WN721N, ath9k_htc, ar9271 fw) on Backtrack 4 R2 distro, running kernel 2.6.35.8, native drivers

Bit rate shown as 1 Mb/s
Can't change bit rate too.

```
#iwconfig wlan0 rate 54M
Error for wireless request "Set Bit Rate" (8B20) :
SET failed on device wlan0 ; Operation not supported.
```

After some digging, I became aware that ath9k driver support is still not mature. Plenty of kinks to be ironed out.

Note to myself - do my homework before getting a wireless adapter next time.](*,)

---

### Post by cman675 on 2011-03-06
I am having the same issue. I bought the TP-Link 2n722N cause I read it had plug and play install in Ubuntu. It installs, but download rate is 1 mb/s. I install AR9271 drivers (since thats the chipset), but if I go to connection information, it says the driver is "usb". Could this be it? How can I force it to use the AR9271 drivers? Thanks so much for the help! 

I am on Ubuntu 10.10 with kernel 2.6.37-020637rc2-generic

---

### Post by TVAbuntu on 2011-05-22
>  it says the driver is "usb"

That's just generic statement from network manager. It's using the driver. You can check by using lsmod.


Anyway, I noticed that there is new firmware listed on linux-wireless, specifically the htc_ar9271.fw, so I downloaded, placed it in /lib/firmware and renamed ar9271.fw to ar9271.bk, but the driver failed to load it (dmesg output: failed to load firmware error 22).

I then recompiled the latest compat-wireless, and tried again. Unloaded the module ath9k_htc, and reloaded. Same error. Tried it with a reboot instead. No dice. Renamed htc_ar9271.fw to just ar9271.fw to try to trick the driver to load it, but nothing.

If anyone has been able to get this new firmware to load, or any insights, please post.

---

### Post by h3mp3r on 2011-10-21
Hi,
Just bought a TP-LINK TL-WN721N (AR9271, USBID 0cf3:9271) and had the same problem.

I got the 1.3 firmware by downloading and compiling the latest [compat-wireless-2.6]("http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2")
```

$ tar xvf compat-wireless-2.6.tar.bz2
$ cd compat-wireless-2011-10-21.tar.bz
$ ./scripts/driver-select ath9k_htc
$ make
$ sudo make install
$ modprobe ath9k_htc

```

and now I have higher rates
```

$ iw wlan1 link
Connected to 00:26:44:**:**:** (on wlan1)
	SSID: Thomson******
	freq: 2447
	RX: 61101385 bytes (59240 packets)
	TX: 2749647 bytes (29408 packets)
	signal: -83 dBm
	tx bitrate: 11.0 MBit/s

```

hope it helps someone

---

