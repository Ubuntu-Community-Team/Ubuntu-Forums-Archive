---
title: "Karmic: How can I make a Bluetooth device *not* auto-connect?"
date: 2010-03-05
forum: Networking &amp; Wireless
---

### Post by original_MikZ on 2010-03-05
G'day peeps,

I have a nifty new headset (a JawBone icon—the noise cancellation is incredible) and I've successfully connected it to my Karmic laptop (64 bit, for the off chance it makes a difference). The trouble is, I only occasionally want to connect it to my laptop; I mostly use it with my mobile 'phone.

The two devices fight over my new toy a lot, and invariably the laptop wins, contrary to what I want. It seems a pain to have to rediscover the headset every time I want to use VIOP or whatever, so is there a way to add a device to Karmic's Bluetooth list, but not have it connect whenever it sees it?

Thanks,
MikZ

---

### Post by Post Monkeh on 2010-03-05
> **original_MikZ said:**
> G'day peeps,

I have a nifty new headset (a JawBone icon&#8212;the noise cancellation is incredible) and I've successfully connected it to my Karmic laptop (64 bit, for the off chance it makes a difference). The trouble is, I only occasionally want to connect it to my laptop; I mostly use it with my mobile 'phone.

The two devices fight over my new toy a lot, and invariably the laptop wins, contrary to what I want. It seems a pain to have to rediscover the headset every time I want to use VIOP or whatever, so is there a way to add a device to Karmic's Bluetooth list, but not have it connect whenever it sees it?

Thanks,
MikZ

i think one of the other bluetooth managers (try bluez-gnome or blueman) gives you a few more options than the default manager, one of which is setting devices as automatically authorise without confirmation. if this was turned off it may sort your problem.

i don't really want to install it myself because i've a few different things set with my bluetooth that i don't want to screw up the settings of, but it;s pretty easy to install and may help you out.

---

### Post by original_MikZ on 2010-03-14
:)

---

### Post by original_MikZ on 2010-03-14
> **Post Monkeh said:**
> i think one of the other bluetooth managers (try bluez-gnome or blueman) gives you a few more options than the default manager, one of which is setting devices as automatically authorise without confirmation. if this was turned off it may sort your problem.

i don't really want to install it myself because i've a few different things set with my bluetooth that i don't want to screw up the settings of, but it;s pretty easy to install and may help you out.
The interface isn't great&#8212;lots of icons whose meanings aren't immediately clear&#8212;but it solved my problem. Thanks!

---

### Post by Post Monkeh on 2010-03-14
yeah, i think it was a bit more awkward to use, that's why i stuck with the default bluetooth manager.
glad it sorted your issue.

---

