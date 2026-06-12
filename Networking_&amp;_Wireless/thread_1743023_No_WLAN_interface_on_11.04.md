---
title: "No WLAN interface on 11.04"
date: 2011-04-29
forum: Networking &amp; Wireless
---

### Post by megabuffen on 2011-04-29
Today I upgraded from 10.10 to 11.04. After accidentally turning off the computer during the upgrade:(, booting into recovery mode:confused:, remounting the file system as writable:) and finishing the upgrade:o, it worked just fine.:D

However, I can no longer use any wireless networks. Wired ethernet works fine, but the wireless inteface won't even show up when I run ifconfig. When I first installed 10.10, it worked instantly and I was able to use it during installation.

I have an HP Compaq nx7300 laptop with a Broadcom BCM4311 network card.

Any ideas?

---

### Post by megabuffen on 2011-04-29
I was eventually able to find a solution in this thread: [http://ubuntuforums.org/showthread.php?t=1741737](http://ubuntuforums.org/showthread.php?t=1741737).

I made a slight change and this is what I typed into the terminal, as root.

```
apt-get -y install b43-fwcutter firmware-b43-installer --force-yes
```

```
nano /etc/modules
```
I added b43 to the end of this file.

```
depmod
```

---

### Post by FAIZAN MALIK on 2013-01-07
same problem with me but in dell inspiron n4050

---

