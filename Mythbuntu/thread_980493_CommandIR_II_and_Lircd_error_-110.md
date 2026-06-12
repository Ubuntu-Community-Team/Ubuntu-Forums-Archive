---
title: "CommandIR II and Lircd error -110"
date: 2008-11-12
forum: Mythbuntu
---

### Post by crp724 on 2008-11-12
I just purchased a commandIR II and am having a great amount of difficulty setting it up on Intrepid.

I installed the lirc PPA from superm1.

After killing all lircd processes and then running "lircd -n -H commandir"
lircd gives the following error

lircd-0.8.4a[9838]: lircd(commandir) ready
lircd-0.8.4a[9838]: accepted new client on /dev/lircd
lircd-0.8.4a[10071]: Child Initializing CommandIR Hardware
lircd-0.8.4a[9838]: CommandIR driver initialized
lircd-0.8.4a[10071]: Product identified as CommandIR II
lircd-0.8.4a[10071]: Unable to read version request - Is CommandIR busy? Error -110


and it keeps repeating the last two lines. irw does not respond to anything despite a good lircd.conf and hardware.conf

Any ideas or help?

The green A light is on but I only get a red light with a keypress on my remote.

Thanks

---

