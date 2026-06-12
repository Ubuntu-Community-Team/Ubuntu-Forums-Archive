---
title: "Lenovo T60, Intel 3945 Wifi Problems on Ubuntu 12.10 LTS"
date: 2012-10-01
forum: Networking &amp; Wireless
---

### Post by bunnye on 2012-10-01
I tried everything to get the wifi working on lenovo t60, intel 3945.
  

Thank you and appreciate any ideas.
  

Did not work: [http://www.dotkam.com/2008/11/17/configure-iwl3945-driver-on-ubuntu/](http://www.dotkam.com/2008/11/17/configure-iwl3945-driver-on-ubuntu/)
[URL="http://www.dotkam.com/2008/11/17/configure-iwl3945-driver-on-ubuntu/"]
[/URL]
  Upload to pastebin: [http://pastebin.com/0VAPi1CN](http://pastebin.com/0VAPi1CN)
  

Ubuntu lover

---

### Post by mikewhatever on 2012-10-03
Can you post the output of **modinfo -F parm iwlwifi**. That seems to be the wireless module for that machine, and not iwl3945. The output will show available options we can work with. Also, if you still have ndiswrapper installed, remove it.

---

### Post by bunnye on 2012-10-04
> **mikewhatever said:**
> Can you post the output of **modinfo -F parm iwlwifi**. That seems to be the wireless module for that machine, and not iwl3945. The output will show available options we can work with. Also, if you still have ndiswrapper installed, remove it.

No worries, after a troubleshooting for a long time, it was working intermittently. Then, I decided to backup the and reinstall 12.04 LTS fresh from CD and all is well now.

To all users, Upgrade from 11.XX to 12.04 is the main cause for the problem, I think.

Thanks for responding...

---

