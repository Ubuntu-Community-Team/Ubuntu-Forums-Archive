---
title: "iMon PAD and lirc not working"
date: 2009-06-22
forum: Multimedia Software
---

### Post by petzler on 2009-06-22
Hi,

the iMon PAD doesn't work:
```

$ irw /dev/lircd

```

doesn't show any IR codes. On syslog I see:

```

$ cat  /var/log/syslog
Jun 22 20:53:22 htpc lircd-0.8.4a[5512]: accepted new client on /dev/lircd
Jun 22 20:53:22 htpc lircd-0.8.4a[5512]: could not get file information for /dev/lirc0
Jun 22 20:53:22 htpc lircd-0.8.4a[5512]: default_init(): No such file or directory
Jun 22 20:53:22 htpc lircd-0.8.4a[5512]: Failed to initialize hardware

```

What happend here? I don't have /dev/lirc0 device:

```

$ ll /dev/li*
srw-rw-rw- 1 root root 0 2009-06-22 20:43 /dev/lircd

```

lsmod gets
```

$ lsmod |grep lirc
lirc_imon              26124  0
lirc_dev               22088  1 lirc_imon

```

Maybe useful informations:

```

$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 9.04
Release:        9.04
Codename:       jaunty
$ uname -a
Linux htpc 2.6.28-13-generic #44-Ubuntu SMP Tue Jun 2 07:55:09 UTC 2009 x86_64 GNU/Linux

```

The informations on web seems to be rather than old - I've lirc 0.84. What can I do to get it working?

Thanks,
Olaf

---

### Post by petzler on 2009-06-23
OK; more info:

USB ID is iMON 15c2:0034. Obviously SoundGraphics changed the IR Receiver which isn't supported in 0.84. First tests with lirc 0.85 got a device lirc{0,1}. But it's still not working, even irw.

Olaf

---

