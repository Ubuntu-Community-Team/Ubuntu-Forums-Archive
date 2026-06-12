---
title: "Trouble with wireless on 9.10"
date: 2009-11-15
forum: Networking &amp; Wireless
---

### Post by Scott496 on 2009-11-15
Hey everyone,
I'm having trouble getting my wireless working with ubuntu 9.10. My wireless card is a Broadcom 4312 but when I try and install the driver as per [this]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Instructions") guide I get an error when I try and install ndiswrapper-utils-1.9. The terminal tells me that it couldn't find the package. Help?

---

### Post by The Toxic Mite on 2009-11-16
Hey! Can you go to Applications > Accessories > Terminal and post the outputs of the following commands please?

```

sudo lshw -c network
lspci
iwconfig

```

Thanks :-)

---

### Post by t0mppa on 2009-11-16
The page is a little outdated, as you can see the Ubuntu versions refer to 3-4 versions back and the other native driver blacklisted there (bcm43xx) is deprecated and not used anymore. I tried that route primarily with my friends Broadcom card, while it worked ok at first, was unable to get WPA2 working with the drivers specified there. Then turned to the native Linux driver (b43, but also the Broadcom STA is available for your card) and that has worked just fine ever since.

---

