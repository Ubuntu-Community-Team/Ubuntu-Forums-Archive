---
title: "Acer laptop - Wireless worked in LiveCD, Does not work after installation."
date: 2009-10-03
forum: Networking &amp; Wireless
---

### Post by npodges on 2009-10-03
I just installed the 9.10 beta on an Acer Aspire 5100.
It has broadcom wireless.
In the liveCD, the restricted drivers manager found two drivers for the card, one of which seemed to do nothing, and the other enabled wireless without any problems.

I forget the name of the first driver, but it said something about getting firmware from cards.

The second driver was the Broadcom STA wireless driver. This one seemed to enable the card.


Now, I have installed ubuntu to the disk, and I cannot enable wireless.
The restricted drivers manager only finds one driver now, Broadcom STA Wireless driver.
The other package is no longer shown.

How can I reenable wireless networking?

Thank you,

Nick

---

### Post by npodges on 2009-10-03
I should add:
The wireless chip is a Broadcom 4311, which is listed as supported by the Broadcom STA driver, which does show up in the restricted drivers manager.

However, when I click "Activate", I am prompted for my password, and brought back to the same screen where I am informed that the driver is inactive.

Thanks again.

---

### Post by Coldandwet on 2009-10-30
Hi,

 I had this same problem with a hp netbook. I found the following worked for me: go into synaptic (system > Administration > Synaptic Package Manager), then go to settings > repositories. Uncheck all other software sources and then check the Ubuntu CD-ROM at the bottom (Make sure you have the Ubuntu 9.10 CD in your CD drive). Close the settings window. Reload the package list. Then search for "bcm". There should be one package listed: "bcmwl-kernel-source". Mark it for install and then apply. Exit synaptic, restart your system and then when you log back in you should be able to active your card in the usual way. I don't know why this package is not copied over during install, bit of a bug.

Oh, and remember to re-enable your software source in synaptic once done.

---

### Post by Holyjoely on 2009-10-30
> **Coldandwet said:**
> Hi,

 I had this same problem with a hp netbook. I found the following worked for me: go into synaptic (system > Administration > Synaptic Package Manager), then go to settings > repositories. Uncheck all other software sources and then check the Ubuntu CD-ROM at the bottom (Make sure you have the Ubuntu 9.10 CD in your CD drive). Close the settings window. Reload the package list. Then search for "bcm". There should be one package listed: "bcmwl-kernel-source". Mark it for install and then apply. Exit synaptic, restart your system and then when you log back in you should be able to active your card in the usual way. I don't know why this package is not copied over during install, bit of a bug.

Oh, and remember to re-enable your software source in synaptic once done.
Thanks, the above solution worked for me. Although I downloaded the .deb file and put it onto my Ubuntu machine via USB as I didn't have access to my installation disk. Thanks again.

---

