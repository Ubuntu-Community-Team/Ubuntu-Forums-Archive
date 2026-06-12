---
title: "Getting Atheros Bigfoot Killer E2200 Ethernet working?"
date: 2013-04-28
forum: Networking &amp; Wireless
---

### Post by workaround2 on 2013-04-28
I have looked at [http://ubuntuforums.org/showthread.php?t=2008332](http://ubuntuforums.org/showthread.php?t=2008332)
I don't understand what I should be doing.

I'm using a fresh install of Ubuntu 13.04 don't mind going to 12.04.
```

sudo apt-get install build-essential linux-headers

```
In both Ubuntu 12.04 and 13.04 I had an error stating to select a version. I just selected a random version of linux-headers. Does the version do any thing?

The patching gives no errors. But do recursive paths make a difference?

```
sudo make
make[3]: *** [/home/username/Downloads/compat-wireless-2012-12-18-p/drivers/bcma/main.o] Error 1
make[2]: *** [/home/username/Downloads/compat-wireless-2012-12-18-p/drivers/bcma] Error 2
make[1]: *** [_module_/home/username/Downloads/compat-wireless-2012-12-18-p] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-19-generic'

```
when doing make I get errors.

---

