---
title: "PANU: I am able to connect to the phone but no internet for some reason"
date: 2010-10-20
forum: Networking &amp; Wireless
---

### Post by klemes on 2010-10-20
Hallo everybody,
I am running Ubuntu 10.04 ,bluez 4.65 and blueman 1.21 (note I have purged gnome-bluetooth in favor of the blueman suite).
I try to share my phone's (SonyEricsson XPERIA X1i) mobile broadband through the PANU service that it provides (no DUN bluetooth profile)
with the above laptop using an ISSC KY-BT100 dongle(of questionable quality I am afraid to say).
My problem is that when I connect with network manager it reports the connection as successful I can verify I get an IP ,DNS ,default gateway and all,everything seems alright and initially I am able to ping both ip's and url's when I try to load any site from my browser the connection freezes and I am not able even to ping anything including my phone.
Can anyone shed some light in this situation?
I am doing something wrong,something I overlooked,could the phone be locked or something...????
Thanks in advance for any input....:guitar:

---

### Post by klemes on 2010-10-21
--Note:I had the same issue when connecting to the same phone through USB.

--Update: I was able to establish proper internet connectivity via USB cable to the phone by setting the connection's MTU to the value of '1394' as explained in an other thread in this forum,but still the problem persists in bluetooth PANU connection despite the above settings.
Any help would really be appreciated!!!!:popcorn:

---

### Post by klemes on 2010-10-21
Problem solved by setting the connection's MTU to the bluetooth dongle's aclmtu value!!!!!!!!!

Case solved!!!!!!!!!!:popcorn::popcorn::popcorn: :guitar::guitar::guitar:

---

### Post by roshgorg on 2010-12-06
> **klemes said:**
> --Note:I had the same issue when connecting to the same phone through USB.

--Update: I was able to establish proper internet connectivity via USB cable to the phone by setting the connection's MTU to the value of '1394' as explained in an other thread in this forum,but still the problem persists in bluetooth PANU connection despite the above settings.
Any help would really be appreciated!!!!:popcorn:

i have a samsung mobile phone..i connected to intenet using mobile broadband in 10.04 in my dell studio laptop..but, 10.10, mobile broadband is disabled...how to enable it?

and what have you said about setting the MTU value to 1394..?
plz reply

---

