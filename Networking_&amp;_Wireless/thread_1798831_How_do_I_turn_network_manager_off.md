---
title: "How do I turn network manager off?"
date: 2011-07-06
forum: Networking &amp; Wireless
---

### Post by nick4554 on 2011-07-06
Hello,

I want to temporarily turn off network manager in order to test WICD on my system. The only tuts online I can find involve uninstalling Network manager, which I dont want to do.

so how do I turn off Network manager (and turn it back on again)?

Thanks.

---

### Post by Iowan on 2011-07-06
Under System>Preferences>Startup Applications is a checkbox for Network Manager. What happens if you uncheck it - then restart/reboot?
I haven't tried it - so I can't say if WICD will overwrite things and make re-enabling NM impossible...

---

### Post by coffee412 on 2011-07-06
> **nick4554 said:**
> Hello,

I want to temporarily turn off network manager in order to test WICD on my system. The only tuts online I can find involve uninstalling Network manager, which I dont want to do.

so how do I turn off Network manager (and turn it back on again)?

Thanks.

sudo service NetworkManager stop

:p

---

### Post by flash63 on 2011-07-07
Hello,
> **coffee412 said:**
> sudo service NetworkManager stop
something different please

```
sudo service network-manager stop (start)
```
... or klick right on the NM icon in the upper panel an disable network.

---

### Post by nick4554 on 2011-07-08
Thanks!

---

