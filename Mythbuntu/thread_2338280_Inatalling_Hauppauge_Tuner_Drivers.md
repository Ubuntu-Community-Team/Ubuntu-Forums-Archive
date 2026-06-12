---
title: "Inatalling Hauppauge Tuner Drivers"
date: 2016-09-26
forum: Mythbuntu
---

### Post by eric-jazzandcoffee on 2016-09-26
Hello,

I tried to install the drivers off some wiki. Not sure if it came off of Mythbuntu website or not. But I ran into a dead end. How so I get my Hauppauge drivers installed correctly? And these are popular cards, why aren't the drivers built in?

THank you.

---

### Post by Bucky Ball on 2016-09-26
> **eric-jazzandcoffee said:**
> ... these are popular cards, why aren't the drivers built in?

How do you know they're not?

Welcome. Switch off the machine and unplug the TV dongle. Switch on the machine and boot into Ubuntu. Plug the device in and give the output of this command from a terminal immediately, without doing anything else.

```
dmesg
```

Check the output at the bottom. What does it say about the device you've just plugged in? Does it say it is configured and has loaded a driver? Copy any relevant bits and post here between code tags (see the link in the first line on my signature at the bottom of this post for how).

Also provide the output of this command with the dongle plugged in:

```
lsusb
```

PS: It will help your cause greatly if you can be clear and specific about what release and flavour of Ubuntu you are using, what exactly your issue is and what you've done to try and fix. 'Tried something from some web page' is not specific enough for us to have any idea what you might have done that could have helped or hindered and nothing to go on with.

---

