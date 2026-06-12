---
title: "Why Does Ubuntu 9.10 hate my HTC FUZE ?"
date: 2009-12-18
forum: Networking &amp; Wireless
---

### Post by cleatus99 on 2009-12-18
Ok,
 I've been messing with Ubuntu for ~4 years now, I had a HTC TILT phone worked great, I upgraded to a HTC Fuze and that's when the trouble started.

 In Ubuntu 8.10 There was a work around to make my phone work tethered, now in 9.10 it seems there is no work around possible.

 I've tried USB tethering, works with old Ubuntu 8.10 with RNDIS Lite changes detailed in thread [http://ubuntuforums.org/showthread.php?t=1074090](http://ubuntuforums.org/showthread.php?t=1074090)

I loaded the Wifi Sharing mobile app, it turns my phone into a mobile ad-hoc access point using WEP 10 digit key.

It doesn't work with Ubuntu 9.10 Either HP Laptop or Dell Mini 9.

Acts as if it can't get password.
On Windows XP Both tethering & Wifi ad-hoc work.

when connected with tethering, I can ping IPs. However I can not get data of any size, sometimes I can get a text only HTML page.
It appears as if there is a larger Data Packet size coming from the HTC Fuze.

Beating my head against the wall:-k Any ideas from the gurus ?

---

### Post by SaintDanBert on 2010-01-25
> **cleatus99 said:**
> Ok,
 I've been messing with Ubuntu for ~4 years now, 
...
I upgraded to a HTC Fuze and that's when the trouble started.

...
Beating my head against the wall:-k Any ideas from the gurus ?

**Sadness** I just got a Fuze and hoped that new-er meant better luck for tether and other.

For me there are several parts to this:
[list]
[*]karmic see fuze and "connect" as ersatz usb-drive
[*]sync contacts, calendar, tasks between fuze and karmic desktop apps (Evolution?) or (Thunderbird?) or ...
[*]karmic access internet through fuze (traditional tether) as only connection
[*]fuze access internet through karmic (access share) if wire or wifi already present
[*]fuze provide "access point" for a few (2 or 3) laptops when meeting away from other internet access [This is preferred over "traditional tether" as a long range solution.]
[/list]

Which, if any, of these do you have working?
What is required on ubuntu karmic to get these working?
What is required (apps) on fuze to get these working?

~~~ 0;-Dan

---

### Post by cleatus99 on 2010-01-25
> 

karmic see fuze and "connect" as ersatz usb-drive 
sync contacts, calendar, tasks between fuze and karmic desktop apps (Evolution?) or (Thunderbird?) or ... 
karmic access internet through fuze (traditional tether) as only connection 
fuze access internet through karmic (access share) if wire or wifi already present 
fuze provide "access point" for a few (2 or 3) laptops when meeting away from other internet access [This is preferred over "traditional tether" as a long range solution.] 

Haven't tried to sync, 
Can't tether, USB 
Wifi Sharing doesn't work with Ubuntu, doesn't like 10 digit key?

---

