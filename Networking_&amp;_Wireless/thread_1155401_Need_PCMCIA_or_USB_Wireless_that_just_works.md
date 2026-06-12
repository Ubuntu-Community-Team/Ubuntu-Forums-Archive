---
title: "Need PCMCIA or USB Wireless that just works"
date: 2009-05-10
forum: Networking &amp; Wireless
---

### Post by mdcollier on 2009-05-10
I've had Ubuntu on an old Toshiba Satellite for about a year, applying upgrades as they came along, and life was good. I got a little frisky today and did an Etch-A-Sketch install of Jaunty. Now my wireless card doesn't work. I have zero interest in any heroics to get the old card to work. What I'm looking for is a recommendation for a high quality PCMCIA card or USB adapter that is 100% compatible with Ubuntu 9.04.

Sorry if this is a little grumpy, but I'm a little frustrated at Ubuntu for sabotaging their market by making what should be easy very cryptic.

Any guidance would be greatly appreciated.

---

### Post by dmizer on 2009-05-10
Have a look here: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

Depending on your card, you may simply need to connect to the internet with your wired nic so Jaunty can download the current firmware for your card.

---

### Post by mdcollier on 2009-05-11
That sounds promising. It is a Linksys WPC54GS ver 2.1. How do I update the firmware?

Thanks for your help!

---

### Post by Glaciusor on 2009-05-11
I bought a USB wifi dongle a while ago for my old Win98 tower, and I just recently aquired 4 "obsolete" computers that I am putting Ubuntu on. I decided to try plugging it in and it just worked right away without anything being installed. I can't recall its exact name, but it is a Gigafast wireless USB dongle, and looking for "Gigafast USB wireless" on Google reveals a lot of places where you can get one of these. If the all else fails, you could try this.

---

### Post by mdcollier on 2009-05-11
Okay. I fumbled my way through creating a Linux driver with ndiswrapper, which I've used before, but it's been a while, and I'd forgotten how totally cool it is.

If I run the command again, I get a response tantamount, to no, dummy, you've already done that.

So, now my wireless networks are greyed out. How do I get Ubuntu to look for broadcast SSIDs?

My apologies if changing the topic is a breach of protocol. I was just thinking that there might be those who would be interested in how this played out.

Thanks again for your attention and advice.

---

### Post by dmizer on 2009-05-11
Well, before we resort to manually searching for broadcasts, let's take a look at your current ndiswrapper setup. Please post the output of:
```
ndiswrapper -l
```

---

### Post by mdcollier on 2009-05-12
Appears I underestimated Jaunty. I connected to the Internet via ethernet, and Jaunty automatically found the proprietary driver for my card. I wanted to undo all the tinkering I'd done, so I did an Etch-A-Sketch, connected to the Internet, checked for updates, and the driver showed up and activated with no drama. I even had Nvidia working, but couldn't tame it and turned it off.

Life is good. I'm sorry, Ubuntu developers. Seems I vastly underestimated how far you've come. (That sounds corny, I don't care who you are...)

---

