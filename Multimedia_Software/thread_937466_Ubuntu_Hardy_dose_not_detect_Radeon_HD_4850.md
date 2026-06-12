---
title: "Ubuntu Hardy dose not detect Radeon HD 4850"
date: 2008-10-03
forum: Multimedia Software
---

### Post by bebopcola on 2008-10-03
command:lspci -nn | grep VGA

output:
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Unknown device [1002:9442]



In addition to this I can't find the Restricted Manager... is the manager not installed by default?

Any help would be greatly appreciated

I was looking here:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Install%20from%20ati.com%20(latest%20version%20of%20drivers](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Install%20from%20ati.com%20(latest%20version%20of%20drivers))

But I cannot find the restricted manager... so this did not help

---

### Post by binbash on 2008-10-03
ati drivers support this card after 8.6.you gonna install the drivers from ati (latest 8.9).

TEsts results of this card on linux : 

[http://www.phoronix.com/scan.php?page=article&item=ati_radeonhd_4850&num=1](http://www.phoronix.com/scan.php?page=article&item=ati_radeonhd_4850&num=1)

---

### Post by markbuntu on 2008-10-03
Do not bother with the restricted driver manager for that card, or envy, they will not get you the right drivers. Follow this guide here:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

---

### Post by bebopcola on 2008-10-03
I tried the guide you linked me, I restarted and the drivers did not detect my card and now I am stuck at 800 x 600 resolution :(

I am gonna try this driver...

[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

---

### Post by bebopcola on 2008-10-04
how do you apply this patch? 

[http://www.phoronix.net/downloads/rv770-id.patch](http://www.phoronix.net/downloads/rv770-id.patch)

---

### Post by Yellow Pasque on 2008-10-04
> **bebopcola said:**
> how do you apply this patch? 

[http://www.phoronix.net/downloads/rv770-id.patch](http://www.phoronix.net/downloads/rv770-id.patch)
That's for the open-source "radeon" driver and you won't want to use that anyway. If you can't get the proprietary driver to work, your next best bet is to build the radeonhd driver from source.

When you tried the guide, did you use method 2?

---

