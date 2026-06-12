---
title: "RT3290 kernel 3.10 problems"
date: 2013-05-13
forum: Networking &amp; Wireless
---

### Post by daaatz on 2013-05-13
Hi,

I migrated to kernel 3.10.0-031000rc1-generic,
on 3.2 wifi works fine, but I had problems with hanging system while developing apps so migratd to 3.6.6 but on 3..6.6 after connectiong wifi system hangs..
So I migrated with kernel to newer version and while compiling drivers I had:

```

/home/maciej/Toolz/stery/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/pci_main_dev.c:71:1: error: ‘__mod_pci_device_table’ aliased to undefined symbol ‘rt2860_pci_tbl’
cc1: some warnings being treated as errors
make[2]: *** [/home/maciej/Toolz/stery/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/pci_main_dev.o] B&#322;&#261;d 1
make[1]: *** [_module_/home/maciej/Toolz/stery/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux] B&#322;&#261;d 2
make[1]: Opuszczenie katalogu `/usr/src/linux-headers-3.10.0-031000rc1-generic'
make: *** [LINUX] B&#322;&#261;d 2
maciej@maciej-HP-Pavilion-g6-Notebook-PC:~/Toolz/stery/DPO_RT3290_LinuxSTA_V2600_20120508$ 

```

I was reading tutorial : [http://ubuntuforums.org/showthread.php?t=2104690&highlight=rt3290](http://ubuntuforums.org/showthread.php?t=2104690&highlight=rt3290).

I tried also coy firmware to lib/firmware but it doesn work for me..

```

maciej@maciej-HP-Pavilion-g6-Notebook-PC:~$ iwconfig 
eth0      no wireless extensions.

lo        no wireless extensions.

maciej@maciej-HP-Pavilion-g6-Notebook-PC:~$     lspci | grep Network
07:00.0 Network controller: Ralink corp. Device 3290


```

Any one can help ?
Thanks

---

### Post by praseodym on 2013-05-13
Why not using the final 3.9? 3.10 as a 1st release canditate will cause problems.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-raring/)

Using it here on 12.04 without problems.

---

### Post by daaatz on 2013-05-14
Thanks but,
as You said i installed kernel 3.9-raring

```

maciej@maciej-HP-Pavilion-g6-Notebook-PC:~$ uname -r
3.9.0-030900-generic

maciej@maciej-HP-Pavilion-g6-Notebook-PC:~$ iwconfig 
eth0      no wireless extensions.

lo        no wireless extensions.

```

I've made also:
```
git clone git://git.kernel.org/pub/scm/linux/kernel/git/dwmw2/linux-firmware.git sudo cp linux-firmware/rt3290.bin /lib/firmware
```

and reboot but no changes..

---

