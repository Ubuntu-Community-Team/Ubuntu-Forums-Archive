---
title: "fglrx problems"
date: 2009-08-26
forum: Multimedia Software
---

### Post by dbbolton on 2009-08-26
I followed this guide for Jaunty (64 bit): [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

However, jockey didn't detect any restricted drivers available for my system, even though I have a Radeon 9600 based card (and it shows up in lspci). I installed xorg-driver-fglrx manually through aptitude. 

When I run
```

#  dpkg-reconfigure -phigh linux-restricted-modules-`uname -r`
```it just mentions updating initramfs, no errors. But when I run:
```
#  insmod /lib/modules/`uname -r`/volatile/fglrx.ko
```it says no such file or directory. I am using the 2.6.28-15-generic kernel and I have installed its restricted modules and headers.

Upon rebooting, my display flickered with artifacts from the last time X was running (with vesa), then the system completely froze. I couldn't even get to a console with Ctrl+Alt+F1, so I rebooted with the magic sysrq key. This will repeatedly happen until I remove the fglrx package.

---

### Post by dbbolton on 2009-08-26
It appears that my card now has 'legacy' status and only works with version 9.3 of the driver. However, version 9.3 of the driver requires Xorg 7.0-3. Hopefully this will be helpful so someone else. Here is some more specific information on my card

```
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV350 AP [Radeon 9600]  [1002:4150] (prog-if 00 [VGA controller])
```

---

### Post by dbbolton on 2009-08-28
For those so inclined, I managed to get the driver working on Debian lenny i386, stock 2.6.26 kernel. Here is some more info about my xorg and fglrx versions:


```

apt-cache policy xorg
xorg:
  Installed: 1:7.3+19
  Candidate: 1:7.3+19
  Version table:
 *** 1:7.3+19 0
        500 http://ftp.us.debian.org lenny/main Packages
        100 /var/lib/dpkg/status

```

```

apt-cache policy fglrx-source
fglrx-source:
  Installed: 1:8-12-4
  Candidate: 1:8-12-4
  Version table:
 *** 1:8-12-4 0
        500 http://ftp.us.debian.org lenny/non-free Packages
        100 /var/lib/dpkg/status

```

---

