---
title: "HELP: Wireless Network Problem! TP-Link TL-WN322G+"
date: 2010-07-13
forum: Networking &amp; Wireless
---

### Post by icyblade on 2010-07-13
Hey everybody

I'm using Ubuntu 10.04 Lucid Lynx LTS, with kernel 2.6.32-22. 
Days before I bought a wireless adapter: TP-Link TL-WN322G+, but it couldn't work well. 

I tried to use [ndiswrapper]("http://sourceforge.net/projects/ndiswrapper/"), but I failed:
```

icyblade@icyblade-desktop-hsyoi:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

teredo    no wireless extensions.

vboxnet0  no wireless extensions.

```

I also tried to compile the driver in [this page]("http://www.reactivated.net/software/zd1211-vendor/releases/"), but I failed again:
```

make[4]: *** [/home/icyblade/ZD1211LnxDrv_2_22_0_0/src/zd1205.o] Error 1
make[3]: *** [_module_/home/icyblade/ZD1211LnxDrv_2_22_0_0] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/icyblade/ZD1211LnxDrv_2_22_0_0'
make[1]: *** [both] Error 2
make[1]: Leaving directory `/home/icyblade/ZD1211LnxDrv_2_22_0_0'
make: *** [all] Error 2

```

What can I do with it? Thanks!

---

