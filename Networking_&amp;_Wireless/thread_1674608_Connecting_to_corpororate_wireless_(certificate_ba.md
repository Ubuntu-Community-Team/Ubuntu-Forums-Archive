---
title: "Connecting to corpororate wireless (certificate based)"
date: 2011-01-24
forum: Networking &amp; Wireless
---

### Post by amjain on 2011-01-24
Hi

I am trying to connect to wireless in my office from my ubuntu. I checked with IT - as per them our office is using Acess Point networking. On a Windows machine I need to go to some URI in Internet explorer and request a certificate and then install the same. 

I tried doing the same from firefox , but not sure how to proceed further. We dont have any WEP key etc. I tried fiddling with vaious other methods like LEAP, importing the certificate from windows etc. 

Please provide some pointers as to how should I proceed - I hope his must be possible ?

regards,
Amit Jain

---

### Post by MooPi on 2011-01-24
Would this help ?
[http://ubuntuforums.org/showthread.php?t=450327]("http://ubuntuforums.org/showthread.php?t=450327")

---

### Post by amjain on 2011-01-31
I think I did not ask my question corectly. Let me try to rephrase.

At my home the wireless is WEP based and hence when I open my ubuntu the wireles simply asks for password and I am connected. 
But not in office - Admin says its certificated based. 
Where do I place the certificates.

---

### Post by yumgnomeandthensome on 2011-02-13
There is a section for cert's in the networkmgr-applet
however i can't get this to work for me, as i'm supposed to auto grab the cert.

I'm gonna try wicd (or something similar)

---

### Post by yumgnomeandthensome on 2011-02-20
Got it working, more a credentials thing than an ubuntu issue, although it does take about 5 minutes to connect, saying this 
 wpa_supplicant[1046]: WPA: Failed to get master session key from EAPOL state machines
 wpa_supplicant[1046]: WPA: Key handshake aborted

---

