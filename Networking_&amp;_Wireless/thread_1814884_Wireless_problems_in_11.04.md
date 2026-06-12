---
title: "Wireless problems in 11.04"
date: 2011-07-30
forum: Networking &amp; Wireless
---

### Post by Bigneil on 2011-07-30
Hi every one.

I recently decided to update ubuntu on my PC which dual boots W7 and previously 10.04. I have done a clean install from disk of 11.04 but i am having a little trouble finding drivers for my wireless. In previous editions of ubuntu I was able to find the driver through <administation> then <additional drivers>. but with this latest release of ubuntu 11.04 There is nothing in <additional drivers> for my wireless card.  

I am right to suspect that my wireless card is no longer supported and if so what is the solution?

..almost forgot. my card is a (Broadcom BCM4306 802.11 b/g).



cheers

Bigneil

---

### Post by ratcheer on 2011-07-30
Your card is still supported. I am not very familiar with that card, but others will be along to help you.

Tim

---

### Post by Bigneil on 2011-07-30
Thanks for replying.  I just noticed a huge sticky for brodcom 43** wireless cards....Doh!   I'll go and have a read of it.

---

### Post by wildmanne39 on 2011-07-30
Hi, if you need more help post back here.
Thank you

---

### Post by nm_geo on 2011-07-30
Be sure to pay attention to the (rev 2) Or (rev 3).

Here is another site that will help to determine if you need the firmware-b43legacy-installer or the straight firmware-b43-installer.

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

---

### Post by IWantFroyo on 2011-07-30
You can go into Synaptic and search 'b43'.

There will be three firmware packages, each with a list of the cards they support in the description. Your card should be there somewhere.

---

### Post by vikas153 on 2011-07-30
hi everyone sorry to disturb your discussion ...actually i am using airbase-ng tool for having a Rogue AP ......and according to my teacher i need to stop its beacons so that no one could see it (otherwise client will detect two ap with same essid) .........so my question is how to suppress the beacons with this tool (airbase-ng) or with some other tool....


thanks in advance    :)

---

### Post by wildmanne39 on 2011-07-30
Hi vikas153, I am not sure how to do what you need, but you should start your own thread with a good title describing the problem so people will see your thread and help you.
Thank you:)

---

### Post by Bigneil on 2011-07-30
> **IWantFroyo said:**
> You can go into Synaptic and search 'b43'.

There will be three firmware packages, each with a list of the cards they support in the description. Your card should be there somewhere.


That did the trick. [IMG]http://2.bp.blogspot.com/_t5SkdcxhRHg/TLeqitHYMTI/AAAAAAAAAEU/PEgeF90OxUA/s1600/thumbs_up_smiley.gif.jpg[/IMG]


Cheers

---

