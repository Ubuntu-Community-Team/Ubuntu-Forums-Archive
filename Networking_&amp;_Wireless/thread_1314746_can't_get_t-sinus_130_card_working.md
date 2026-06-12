---
title: "can't get t-sinus 130 card working"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by Puddy on 2009-11-04
Hi,

I got a T Sinus 130 card (pcmcia wlan card, not card2, the first one!)

and I would love to use it..
At first it seemed to work, I plugged it in and iwconfig listed an wlan device, but I could not find any networks (but the other laptop next to this one did..)
Then I tried another pcmcia card, which worked immediately. Now, when I plug in just the Sinus card, iwconfig doesn't even list an wlan device anymore.

Since it didn't work out of the box, I tried to use the windows drivers using ndiswrapper. It accepted the .inf but it says there is no hardware matching the driver

```
# ndiswrapper -l
dtnic: driver installed
```

I looked around a lot, but I can't find anything useful concerning this card...

Besides hoping it works out of the box and trying ndiswrapper, what else can I do?
Thanks in advance :)


BTW: I'm not very much experienced in linux

---

