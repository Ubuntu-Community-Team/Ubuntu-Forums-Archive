---
title: "WiFi Help With Dell (BCM4311)"
date: 2009-03-31
forum: Networking &amp; Wireless
---

### Post by Vostrocity on 2009-03-31
Some background: I installed 8.10 a few months back but never really got around to trying it out until yesterday when Vista crashed and burned majorly (that's another story). So to say I'm Windows kid with no Linux experience.

I have a few problems, but the most important one for now is WiFi. Right now I'm tethered to my router by Ethernet, which is no good place to be. :) I'd like to have WiFi going so I can be up in my bedroom. I know there are some threads about this same problem but I haven't found anything definite. I could probably get ndiswrapper to work but I think there's a native solution.

Dell Vostro 1500
Broadcom BCM4311 (rev 1) mini-PCI b/g
I think that's all the specs you need right now.

I saw [this page]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom#miniPCI") which lists my card as compatible and "works out of the box" (last entry). I also saw that Broadcom had got some new drivers for my card [here]("http://www.broadcom.com/support/802.11/linux_sta.php"). I downloaded the tar file which has some random files in there, but being a Linux noob I have no idea what to do with it.

Thanks for any help. First post yay!:cool:

---

### Post by Sam Lars on 2009-03-31
There is a chance your card will work "out of the box."  Does it show up in Network Manager in the tray?

---

### Post by Vostrocity on 2009-04-01
Lol, no it doesn't work "out of the box" or otherwise I wouldn't be asking.

Anyways, thanks for the help but I got it. It turned out that I forgot to update Ubuntu first. After installing the 283 updates and activating the driver it worked.:D Now I'm rockin Ubuntu in my bedroom.

---

