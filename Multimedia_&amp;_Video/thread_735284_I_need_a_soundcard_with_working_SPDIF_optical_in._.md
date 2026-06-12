---
title: "I need a soundcard with working SPDIF optical in. (yes, in, have out only :-)"
date: 2008-03-25
forum: Multimedia &amp; Video
---

### Post by Cracauer on 2008-03-25
The title says it all: I got sound with SPDIF out working, but to my dismay this one actually doesn't have SPDIF in.

Is there any product that I can buy right now that is a ALSA capable  and has working SPDIF optical in?

The list of supported chips isn't too useful as it's almost impossible to find out which chip is on which card.

Ideally, I'd want USB-2.0 but PCI or PCIe will do.

---

### Post by Shazaam on 2008-03-25
Tons of them here, take your pick (even has chipset info)................

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2000360057&bop=And&Order=RATING](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2000360057&bop=And&Order=RATING)

---

### Post by Cracauer on 2008-03-25
> **Shazaam said:**
> Tons of them here, take your pick (even has chipset info)................

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2000360057&bop=And&Order=RATING](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2000360057&bop=And&Order=RATING)

How do you know all of these have working ALSA drivers?

---

### Post by Shazaam on 2008-03-25
Check the chipset listed and see if they are supported.

---

### Post by thebigbluecan on 2008-03-30
Cracauer would you please post what card you got spdif out working on? I would appreciate it. I found an alsa site which may help you with your Quest to find a card....  [http://alsa.opensrc.org/index.php/Alsa_Preferred_Soundcards](http://alsa.opensrc.org/index.php/Alsa_Preferred_Soundcards)  ...   I have Ubuntu and my sound card has spdif out but it doesn't work with Ubuntu. I just need output through spdif. So what card are you using... Thanks.


                                                                                           ~Ted

---

### Post by Cracauer on 2008-05-20
OK, let's try that again.  

Just so that I don't look like a jerk: Shazaam's reply was predictably useless.  I went down the list of newegg cards before I posted, and there's not a single one of them that isn't easily identified as not doing the right thing.  

Does anybody have SPDIF in(!) working with ALSA on a USB or PCI soundcard?  

thebigbluecan, I have SPDIF out working on an Asus A8N-SLI socket 939 mainboard, the integrated sound. Keep in mind I cannot test it as I have no device receiving SPDIF. But ALSA sees the SPDIF output channels and is happy switching to them.

---

