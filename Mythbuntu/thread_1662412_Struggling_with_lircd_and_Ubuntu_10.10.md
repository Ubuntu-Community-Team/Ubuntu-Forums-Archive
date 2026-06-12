---
title: "Struggling with lircd and Ubuntu 10.10"
date: 2011-01-08
forum: Mythbuntu
---

### Post by mbobak on 2011-01-08
Hi,

I'm trying to get lirc working with myth and ubuntu 10.10.

First thing I tried was running 'mythbuntu-control-center' to enable the IR options there.

I've got a Streamzap PC Remote, and that's how I configured it.

No dice.

I did some digging, read how to test lirc.

So, first, stop lircd:
```
sudo /usr/init.d/lirc stop
```

then, run it in nodaemon mode:
```
sudo lircd --nodaemon
```

finally when I run 'irw' in a different window, it appears to connect, but back in the window where lircd is running, I get:
```
lircd-0.8.7-pre3[2939]: lircd(default) ready, using /var/run/lirc/lircd
lircd-0.8.7-pre3[2939]: accepted new client on /var/run/lirc/lircd
lircd-0.8.7-pre3[2939]: could not get hardware features
lircd-0.8.7-pre3[2939]: this device driver does not support the LIRC ioctl interface
lircd-0.8.7-pre3[2939]: make sure you use a current version of the driver
lircd-0.8.7-pre3[2939]: Failed to initialize hardware

```

I've been googling and looking around for while now...can anyone clue me in on what's going on here?

Thanks,

-Mark

---

### Post by mbobak on 2011-01-09
Ok, this is resolved.

Even though I'm running 10.10, and I'm fully updated, and I have the 2.6.35-24 kernel installed, grub kept booting 2.6.32-24, which doesn't have an updated streamzap driver.

I upgraded to grub2 and then I was able to boot 2.6.35-24, which gave me the appropriate version of the streamzap driver.  Problem solved.

-Mark

---

