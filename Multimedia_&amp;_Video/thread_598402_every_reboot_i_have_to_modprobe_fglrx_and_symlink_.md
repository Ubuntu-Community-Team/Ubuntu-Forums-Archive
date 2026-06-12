---
title: "every reboot i have to modprobe fglrx and symlink it.. what gives?"
date: 2007-10-31
forum: Multimedia &amp; Video
---

### Post by fizz on 2007-10-31
I have to symlink my fglrx.ko file
ln -s /lib/modules/2.6.22-generic/misc/fglrx.ko /lib/modules/2.6.22-generic/volatile/fglrx.ko
modprobe fglrx

Any idea why this has started to happen? it was fine until a couple days ago.. Thanks in advance.. Also, some how my /etc/default/linux-restr file keeps removing fglrx from disabled so it starts to load the other driver from time to time.

Thanks in advance.

ps. I was using envy, removed driver with envy and manually installed the latest and am running aiglx

---

### Post by fizz on 2007-11-05
bump


I added the symlink to my rc.local and added fglrx to /etc/modules, but still have to modprobe it when i start.

---

