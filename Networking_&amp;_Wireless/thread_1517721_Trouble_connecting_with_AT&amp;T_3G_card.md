---
title: "Trouble connecting with AT&amp;T 3G card"
date: 2010-06-25
forum: Networking &amp; Wireless
---

### Post by IceDoE on 2010-06-25
A group I'm working with recently got new netbooks with Ubuntu Netbook Edition 10.04 and some AT&T LaptopConnect (3G) cards. When I hook them into the usb port, the cards light begins blinking, but nothing shows up to indicate ubuntu has recognized the new card, nor am I able to connect to the internet. My searches for help have indicated no one else has had any difficulty with this and that the card usually pops up and installs some drivers automatically or something.

Any help getting these cards up would be appreciated. I'm not sure at the moment the model of the 3G card other than very new, but I can check on that in a bit. The netbooks are HP Mini 210s.

---

### Post by ieee488 on 2010-06-25
> **IceDoE said:**
> My searches for help have indicated no one else has had any difficulty with this and that the card usually pops up and installs some drivers automatically or something.

No one has any difficulty in **Windows**.

I have a similar device from T-mobile. Fortunately, it works with Ubuntu, but I had to do some Googling.

You'll need to Google for information about that model with regards to Ubuntu.

---

### Post by IceDoE on 2010-06-26
No, I meant no one seems to have had issues in Ubuntu either. I saw plenty of people posting it was easier for them to get going in Ubuntu than in Windows.

I saw some people reporting issues maybe 2-3 years ago, but it all seemed issues that were no longer relevant since upgrades and such, and not with newer cards that I can find.

I'll try to do some more searching again, but I have done so with the specific model and for ubuntu and ubuntu netbook edition a few days ago and only found a couple people asking questions if it worked and several people saying "it worked as soon as I plugged it in" or "it popped up the instructions and downloaded all the necessary files for me". Not that helpful of course when that isn't happening in this case.

---

### Post by ieee488 on 2010-06-26
Apparently there are different models of these devices from AT&T just as there are with those from T-mobile.

[http://ubuntuforums.org/showthread.php?t=1478676](http://ubuntuforums.org/showthread.php?t=1478676)
discusses one made by LG; is yours made by LG?

---

### Post by IceDoE on 2010-06-26
Yea, a bit after I posted I was able to get my hands on one of the cards (they gave it to all the people that will be using it in the field but they didn't give one to ME who needs to get them running).

Its an LG USBConnect Turbo.

I was able to find some info and get usb modeswitcher going after alot of fiddling around with stuff. However, now I have a new problem which I've seen out there for some other cards it seems: Network Manager detects the card and gives me two options to connect to "AT&T Data Connect 1" and "AT&T Data Connect (Accelerated) 1" When I try to connect to either it immediately says "GSM network: disconnected" and thats it. Saw some stuff where this happened with some other cards or something a while ago but haven't yet located a solution that works.

---

