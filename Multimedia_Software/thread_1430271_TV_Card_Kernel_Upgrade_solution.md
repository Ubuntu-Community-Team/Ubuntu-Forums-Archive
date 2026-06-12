---
title: "TV Card: Kernel Upgrade solution?"
date: 2010-03-15
forum: Multimedia Software
---

### Post by dealcorn on 2010-03-15
Karmic ( kernel 2.6.31) does not support my TV card:

```
~$ lspci -vnn

Multimedia controller [0480]: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder [1131:7133]
```

"1131:7133" is nowhere present in the 2.6.31 SAA7134 cardlist.  However, "1131:7133" is supported as card 17 under a different card name within kernel 2.6.33, see [HTML]http://www.mjmwired.net/kernel/Documentation/video4linux/CARDLIST.saa7134[/HTML].  

Where do I look for guidance on such a kernel upgrade?  My impression is that grub permits booting to an earlier kernel so a boo boo is recoverable.  While not particularly relevant, my card is a Chronos Video Shuttle II.

---

### Post by Yellow Pasque on 2010-03-15
32-bit:
```
cd ~/
mkdir kerneldebs
cd kerneldebs/
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/linux-headers-2.6.33-020633-generic_2.6.33-020633_i386.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/linux-headers-2.6.33-020633_2.6.33-020633_all.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/linux-image-2.6.33-020633-generic_2.6.33-020633_i386.deb
sudo dpkg -i linux*
```

OR

64-bit:
```
cd ~/
mkdir kerneldebs
cd kerneldebs/
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/linux-headers-2.6.33-020633-generic_2.6.33-020633_amd64.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/linux-headers-2.6.33-020633_2.6.33-020633_all.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/linux-image-2.6.33-020633-generic_2.6.33-020633_amd64.deb
sudo dpkg -i linux*
```

---

### Post by dealcorn on 2010-03-16
Immense thanks.  The kernel upgrade worked perfectly.  

As an unrelated follow up, the Chronos Video Shuttle appears to remain unsupported.   README.saa7134 refers to: [HTML]http://www.semiconductors.philips.com/pip/saa7134hl[/HTML] which identifies valid tuners that can be dereferenced to 6 possible tuner numbers by CARDLIST.tuner (both files in /usr/share/doc/linux-doc/video4linux).  I rebooted using each of the 6 in /etc/modprobe.d/saa7134 using the following format:

     options saa7134 card=17 tuner=X
     CONFIG_I2C=m     
     CONFIG_VIDEO_DEV=m

TVtime would not to scan channels.  I give up for now.

---

