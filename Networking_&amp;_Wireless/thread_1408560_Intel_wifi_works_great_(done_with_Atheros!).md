---
title: "Intel wifi works great (done with Atheros!)"
date: 2010-02-16
forum: Networking &amp; Wireless
---

### Post by nray on 2010-02-16
I've had an Acer Aspire One netbook (AOA150-1570) with Atheros wifi that I've been using Ubuntu on for a year, and I finally got fed up with the utterly flakey wifi, and replaced the Atheros card with an Intel WiFi Link 5100 Mini PCIe card.

The difference is night and day.

The Intel 5100 is completely reliable, with high performance, no random drop outs, no disconnects, and most importantly, no hard locks of my entire system that would randomly happen every 1-2 days (which I think is also very likely due to the Atheros drivers).

What drove me to this was that in the last month, the Atheros driver has been worse than ever, with random connection drops - even while within 15 feet of the AP with 100% signal, light traffic, and no WEP/WPA!  It would sometimes happen over and over and over.

The Intel 5100 card I bought for $18 from a seller on ebay, and it was the best $18 I've ever spent.  So much better it's not even funny.

Is this the type of thing that people should be warned about in the [Apsire One wiki entry]("https://help.ubuntu.com/community/AspireOne")?

Is anyone actively working on the Atheros driver problems?  I did some google searches, and it wasn't clear from the bug reports I was reading whether or not these driver stability/performance issues were being dealt with or not.

I can not imagine having a notebook with Atheros wifi and being a first-time Ubuntu user, because I would just hate the experience and not know what the problem was... and the suggestions to manually install the madwifi drivers from a downloaded tar file after disabling the ath5k drivers is beyond what most people should have to deal with.

---

### Post by tcinlo on 2010-02-16
OH MY GOD!!!!! You are talking about me!!!:o I have an Asus, not Acer, but it has the Atheros wifi and it doesn't work and I've been trying to fix it with downloads and installing different drivers and as you said, I shouldn't have to fuss with that.
 
So tell me...is that Intel wifi card you spoke of an internal or external card? Did you have to install any software for it? If it is internal...did you install it yourself? Is it easy to take the cover off my netbook?
 
I have Unbuntu 9.04 loaded and have not tried to drivers yet....I did that on an older version.

---

### Post by nray on 2010-02-16
> **tcinlo said:**
> OH MY GOD!!!!! You are talking about me!!!:o I have an Asus, not Acer, but it has the Atheros wifi and it doesn't work and I've been trying to fix it with downloads and installing different drivers and as you said, I shouldn't have to fuss with that.
 
So tell me...is that Intel wifi card you spoke of an internal or external card? Did you have to install any software for it? If it is internal...did you install it yourself? Is it easy to take the cover off my netbook?
 
I have Unbuntu 9.04 loaded and have not tried to drivers yet....I did that on an older version.

How the wifi hardware works can vary from notebook to notebook... in the Acer Aspire One, it is a mini PCI-Express (PCIe) card, which fits in kind of like a big RAM module.  I do IT work for a living, so I am very versed in hardware and software, and using a few pictoral guides on the internet was able to replace the Atheros mini PCIe card with the Intel fairly easily, but it did require me to take out a lot of small screws and do some delicate work disconnecting and reconnecting things inside my netbook that a lot of people wouldn't be comfortable with.

If you're lucky, the ASUS you have might make the wifi a lot more accessible and replaceable, either under a door or some other easy-access part of the computer, it all depends on what the manufacturer decided to do.

I decided to go with the Intel 5100 specifically because in at least Ubuntu 9.10 (and probably some older versions) there is already support for it out-of-the-box, the drivers are known to be reliable, and it is also an 802.11n card that has connectors for just two antennas (not three like some 802.11 cards, such as the Intel 5300 series).  The Atheros card that comes with the Acer Aspire One is an 802.11g card that has only two antenna connectors, so the Intel 5100 is a good match.

If changing the internal card in your notebook is either too much trouble or not possible, you might consider an external, USB wifi adapter.  On my HTPC I run Ubuntu 9.10 as well, and I use an ASUS WL-167g adapter (based on a RALink chipset) which is supported out-of-the-box in Ubuntu (going back to I think 8.04), and would work almost as well on a notebook as it does on a desktop... with the downsides being that it would be less convenient than an internal solution in a notebook, and I've read that that at least for some people, you have to turn off USB power management or it can cause the wifi connection to have issues (I haven't tried it in my Ubuntu notebook, so I can't say for sure).  It's $17 right now at Newegg:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833320107]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833320107")

---

### Post by tcinlo on 2010-02-16
Thanks, I'm going to look into all you suggested.

---

