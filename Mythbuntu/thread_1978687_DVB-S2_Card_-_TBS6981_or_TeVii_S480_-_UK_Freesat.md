---
title: "DVB-S2 Card - TBS6981 or TeVii S480 - UK Freesat"
date: 2012-05-12
forum: Mythbuntu
---

### Post by roundhay on 2012-05-12
I want to put a DVB-S2 card into my HTPC so I can make use of an old Sky TV dish to watch Freesat in the UK. I was planning to do this a year ago but never got round to it. My previous post and replies are on this thread:

[http://ubuntuforums.org/showthread.php?t=1716556]("http://ubuntuforums.org/showthread.php?t=1716556")

I have done some research and I'm considering buying a

TBS6981 or a TeVii S480 these are both dual tuners and use the PCIe interface.

Before I buy I would like advice on which is the best card to buy.

I have a combined FE/BE machine and I use MythWelcome and  ACPI_Wakeup to automatically wakeup and shutdown the machine to record TV programs.

I have read some posts which describe issues with these cards but I'm not sure if the issues will manifest themselves in my set up.

The issues I am referring to are discussed in these threads

TeVii S480
[http://ubuntuforums.org/showthread.php?t=1924193]("http://ubuntuforums.org/showthread.php?t=1924193")


TBS6981
[http://www.mythtv.org/pipermail/mythtv-users/2012-February/328220.html]("http://www.mythtv.org/pipermail/mythtv-users/2012-February/328220.html")

I'm not certain is the MythWelcome / ACPI_Wakeup uses S3 so I don't know if this is relevant?

[http://www.mythtv.org/pipermail/mythtv-users/2011-March/311819.html]("http://www.mythtv.org/pipermail/mythtv-users/2011-March/311819.html")

[http://www.gossamer-threads.com/lists/mythtv/users/474550]("http://www.gossamer-threads.com/lists/mythtv/users/474550")

I'm not necessarily looking for a card that will work out of the box and I'm happy to work through fixes as long as I will end up with a stable working system.

Any comments and advice appreciated.

---

### Post by AlecJ on 2012-05-12
The TeVii S480 PCI-e card is trouble!
It will work fine but it falls asleep and the only way to wake it is to reboot.
I returned mine to DVBshop (well never got a refund so don't use them EVER!)

TBS on the other hand works well, I have 2 , 1 x tbs 8299 PCI and 1 TBS 6891 PCI-e dual.
Got them both from Amazon at a good price.

You have to load the drivers and reload if there in a new linux image update, but they work well for me.

---

