---
title: "mDNS query packets ?"
date: 2013-02-09
forum: Networking &amp; Wireless
---

### Post by kapetr on 2013-02-09
If I bring up wlan0 device (manualy; NM stopped) I can see in Wireshark mDNS outgoing packets. E.g.:

Standard query ANY: 
my_station_name [a7:ce:09:03:cd:03]._workstation._tcp.local: type ANY, class IN, "QM" question
(type ANY - request for all records)

I have following questions and problems:



**1.** which app sends this packets ? Avahi-daemon ?

**2.** Is it the try to get IP address  in ZeroConf or what ?
 
**3.** the port 5353 is hard-wired allowed in ufw - it is not possible to deny it in user chain! Why is it soooooo necessary ?

**4.** I'm changing MAC address of my wifi card direct in udev config, bud in the mDNS query packet is shown the real HW address a7:ce:09:03:cd:03.

So my try to be anonymous fails! My real MAC is shown in "Name:" attribute of this packets :-(

Why ? SHould I report this as Bug of mDNS app ? Which one ?

**4a.** BTW in NM is allways shown the real MAC address too ?! Why is changed MAC ignored by NM and where gets from NM the orig MAC at all ?


**5.** In Wireshark are shown only IPv6 broadcasts. Why are not send IPv4 too ?

**6.** How to disable entirely that sh.. ? 
I don't know, what is it for in Linux - maybe only in Win/Mac heterogen networks ? 

**7.** The package libavahi-client3 is necessary for almost any app in system ?!
So is here risk of sending such packets by any possible app ? 


Thanks.

---

