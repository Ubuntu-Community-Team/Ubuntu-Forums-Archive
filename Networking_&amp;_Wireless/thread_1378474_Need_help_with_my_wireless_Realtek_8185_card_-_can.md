---
title: "Need help with my wireless Realtek 8185 card - can't make an ad-hoc network!"
date: 2010-01-11
forum: Networking &amp; Wireless
---

### Post by Turin Turambar on 2010-01-11
The card is recognized by Ubuntu 9.10 and I have it in the network manager. 

I followed one tutorial about creating an ad-hoc network and all looked good, until I actually wanted to connect (or to be more precise, my machine is a host for other computers).
The wireless icon just loops endlessly, without connecting and eventually I get "Wireless network - disconnected" message.

So, the main issue here is - connecting! I just can't.
Also if you know/have some good tutorial for ad-hoc, please share it here! Thanks.

```
ivan@ivan-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"internat3"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

---

### Post by Turin Turambar on 2010-01-11
The card won't set "adhoc" mode for unknown reasons.

```
ivan@ivan-desktop:~$ sudo iwconfig wlan0 mode ad-hoc
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Operation not supported.
ivan@ivan-desktop:~$ 

```

Any ideas? What to try next? What's happening?

---

### Post by Turin Turambar on 2010-01-12
bump

---

