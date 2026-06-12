---
title: "Acer Aspire 1 Wireless router question."
date: 2009-09-02
forum: Networking &amp; Wireless
---

### Post by larrinski on 2009-09-02
I bought an Acer Aspire one the other day and nuked Windows XP. Yah! 

I put Jaunty on it and everything seems to work out of the box(big improvement in performance over XP), except one thing. I **can't** connect to one particular wireless basestation at my local coffee shop. It has a WPA/WPA2 password. Yes, I know the password. :) After it tries for a couple of minutes, the network connector pops up. When I unmask the password it has been replaced with a huge long scrambled one. Normal? 

My Apple Airport at home has a WPA2 password and I connect to that just fine, so my question(s) is:

How do I find out what the base station is at the coffee shop and if for some reason it has a compatibility issue with my wireless card? Or, is there something I can try to get the base station to accept my password?

My card is the Atheros AR242x. I am running 9.04. 

Cheers!

---

### Post by warreno on 2009-09-05
If I recall, there are two types of WPA protection: Personal and Enterprise. I believe they have different levels of encryption. (128 vs. 256 bit?) Might be worth checking to see if your cafe is using the Enterprise level of WPA, and choosing that from the connection type.

I don't have my netbook (also an Aspire One) open and in front of me right now, so I'm not sure what set of options to choose from in the networking controls.

And yes, it's not unusual for your password to look bizarre after you unmask it; it's actually a hexadecimal string, not a human-readable one. The "plain text" password is there to make it much easier to remember. Something like "cafe_password" is a lot easier to get right than "0f22aa1b37247e" or what have you.

Hope this helps...

---

