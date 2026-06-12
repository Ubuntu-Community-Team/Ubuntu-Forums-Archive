---
title: "Problem with wireless drivers to work with host ap"
date: 2011-08-04
forum: Networking &amp; Wireless
---

### Post by f.constantino on 2011-08-04
Greetings,

I am trying to set up my laptop to work as an AP, given the work I need to do for my theses. As far as I've searched and read many posts/tutorials I have come to the conclusion that the program "hostapd" is required to do such a thing. 

I've tried following several tutorials to make this work, but I never seem to get it working and I believe it's because of my wireless card (though I'm not sure :x). From what I saw, one of the requirements for hostapd to work is when I do $ iw list , I would have to receive an output saying: 

 "Supported interface modes:
...
* AP
..."

and mine doesn't have AP as a supported mode.

My wireless card is Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01).

Can someone please tell me if this card is not able to go into AP mode at all, or if it's a driver issue, and if so, a little help would be very helpful.
Edit: I am using Ubuntu 11.04

Thank you,
Fábio.

---

### Post by f.constantino on 2011-08-04
I've also been fiddling around with compat-wireless drivers trying to get this to work, but again, no success :(

---

### Post by westie457 on 2011-08-11
> **f.constantino said:**
> Greetings,

I am trying to set up my laptop to work as an AP, given the work I need to do for my theses. As far as I've searched and read many posts/tutorials I have come to the conclusion that the program "hostapd" is required to do such a thing. 

I've tried following several tutorials to make this work, but I never seem to get it working and I believe it's because of my wireless card (though I'm not sure :x). From what I saw, one of the requirements for hostapd to work is when I do $ iw list , I would have to receive an output saying: 

 "Supported interface modes:
...
* AP
..."

and mine doesn't have AP as a supported mode.

My wireless card is Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01).

Can someone please tell me if this card is not able to go into AP mode at all, or if it's a driver issue, and if so, a little help would be very helpful.
Edit: I am using Ubuntu 11.04

Thank you,
Fábio.

Hi this is probably a driver issue. Do you know which driver you have installed?

---

