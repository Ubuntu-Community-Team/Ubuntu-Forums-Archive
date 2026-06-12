---
title: "Intel wireless and router death. A minor rant and plea for a fix"
date: 2012-05-31
forum: Networking &amp; Wireless
---

### Post by ricegee on 2012-05-31
First post and I must say I'm disappointed.

I tried Ubuntu 11.10 and it was alright but it had a major issue on my laptop. Using the Intel wireless would take down any wireless router it would hook up to in "n" mode. The solution was to follow [this]("http://elijatech.wordpress.com/2012/03/26/stop-ubuntu-11-10-killing-your-network/").

Now I am trying 12.04 and the situation has got worse. Ubuntu (and it seems other distros) still has a very bad effect on routers but now the fix only works until the computer is rebooted. Internet cafes, train stations and coffee shops are all starting to hate me as I destroy their wireless by using Ubuntu!

Earlier, I said I was disappointed and what I am disappointed about is the fact that such a serious bug is still not fixed and in fact has got worse. I suppose canonical has been to busy with their interface experiment to fix something that serious.

If I haven't worn out my welcome, is there a permanent fix for this issue?

Wireless card as identified by lspci
```
01:00.0 Network controller: Intel Corporation Centrino Wireless-N 130 (rev 34)
```

---

### Post by chili555 on 2012-05-31
The name of the module in 12.04 is *iwlwifi* and not *iwlagn*. Did you change your .conf file? I wish I could tell you there is a permanent fix. You might comment here:  [http://bugzilla.intellinuxwireless.org/](http://bugzilla.intellinuxwireless.org/) > I suppose canonical has been to busy with their interface experiment to fix something that serious.Canonical is not the author of the driver nor the firmware:```
chili@LAPTOP60:~$ modinfo iwlwifi
filename:       /lib/modules/3.2.0-24-generic-pae/updates/cw-3.3/iwlwifi.ko
alias:          iwlagn
license:        GPL
[COLOR="Red"]author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>[/COLOR]
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
<snip>
```

---

