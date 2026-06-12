---
title: "Cannot set an Atheros AR9285 wireless card (ath9k driver) to master mode"
date: 2010-08-09
forum: Networking &amp; Wireless
---

### Post by Birion on 2010-08-09
Hi,
I've been trying to set up a router, following the directions on [https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router). Unfortunately, the darn wireless card is acting up. Despite the information on [http://wireless.kernel.org/en/users/Drivers/ath9k](http://wireless.kernel.org/en/users/Drivers/ath9k), every attempt to set it into a master mode results in this error:

```
sudo iwconfig wlan0 mode master
```

```
Error for wireless request "Set Mode" (8B06) :
   SET failed on device wlan0 ; Invalid argument.
```

I tried to look around, but most of the identical problems seem to be 2 to 4 years old, and the workarounds mentioned refer to webpages lost to time.

---

### Post by Avraham0 on 2010-09-29
Same problem here, any success setting it to master mode?

---

### Post by iClouseau88 on 2010-09-29
Why not try "...mode manage"?

---

### Post by markturnip on 2011-01-08
Did you ever work this out?

---

### Post by winckler on 2011-03-02
(Sorry to resurrect this old thread, I hope it help)

The problem is that iwconfig is unable to deal with the mac80211 framework. (Ref: [https://help.ubuntu.com/community/WifiDocs/MasterMode](https://help.ubuntu.com/community/WifiDocs/MasterMode))

You should use "iw". I also suggest "hostapd" ([http://linuxwireless.org/en/users/Documentation/hostapd](http://linuxwireless.org/en/users/Documentation/hostapd)).

I've successfully setup an AP with an Atheros AR9285 wireless card.

Regards,
Winckler

---

### Post by jogl on 2012-01-02
Hi Winckler,

can you post your working configfile?

thx in advance
cheers
jogl

---

### Post by jogl on 2012-01-05
I've solved my problems. Let's do hostapd the magic... Then I have no problems. Hostapd set the correct modes.

---

### Post by hiteshkc on 2012-01-09
I am not able to run hostapd with my config file, here is my hostapd config file 
hostapd.conf
interface=wlan2
driver=ath9k_htc
ssid=MyAP
hw_mode=g
channel=11
wpa=1
wpa_passphrase=MyPasswordHere
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP CCMP
wpa_ptk_rekey=600

it gives somthing strange 

hitesh@hitesh-IPM41-D3:~$ sudo hostapd -dd /etc/hostapd/hostapd.conf
Configuration file: /etc/hostapd/hostapd.conf
Line 2: invalid/unknown driver 'ath9k_htc'
1 errors found in configuration file '/etc/hostapd/hostapd.conf'
 
Is there any body who can help me out to come out from this problem .

Thanks in advance

Hitesh Kumar

---

### Post by Xers on 2012-02-10
> **hiteshkc said:**
> I am not able to run hostapd with my config file, here is my hostapd config file 
hostapd.conf
interface=wlan2
driver=ath9k_htc
ssid=MyAP
hw_mode=g
channel=11
wpa=1
wpa_passphrase=MyPasswordHere
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP CCMP
wpa_ptk_rekey=600

it gives somthing strange 

hitesh@hitesh-IPM41-D3:~$ sudo hostapd -dd /etc/hostapd/hostapd.conf
Configuration file: /etc/hostapd/hostapd.conf
Line 2: invalid/unknown driver 'ath9k_htc'
1 errors found in configuration file '/etc/hostapd/hostapd.conf'
 
Is there any body who can help me out to come out from this problem .

Thanks in advance

Hitesh Kumar


Hey Hitesh

The answer to your problem is that you've set your  driver=ath9k_htc.
Change it to nl80211
driver=nl80211
hope this will help..;)

---

