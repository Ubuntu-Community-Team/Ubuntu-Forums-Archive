---
title: "rtl8185 problems while manually loading module"
date: 2006-01-14
forum: Networking &amp; Wireless
---

### Post by kasemodz on 2006-01-14
Alright I went to the realtek sourceforge project and I used this howto.
[http://ubuntuforums.org/showthread.php?t=95879&highlight=rtl8180+error]("http://ubuntuforums.org/showthread.php?t=95879&highlight=rtl8180+error")

So I downloaded the tar file and installed the deb. Then I dpkg it. After that I decided to manually load the modules. 
I was able to manually laod tw of the four modules. I loaded these modules.
> insmod /lib/modules/2.6.12-10-386/kernel/net/rtl8180/ieee80211_crypt-r8180.ko

and
> insmod /lib/modules/2.6.12-10-386/kernel/net/rtl8180/ieee80211_crypt_wep-r8180.ko


However, when I tried to manually load the these two modules I got an error.
Here are thw two modules that couldn't be loaded.
> insmod /lib/modules/2.6.12-10-386/kernel/net/rtl8180/ieee80211-r8180.ko

and
> insmod /lib/modules/2.6.12-10-386/kernel/net/rtl8180/r8180.ko

I got this error on both modules
> Unknown Symbol in module

I did some more digging and I went to /lib/modules. There I saw two folders- 2.6.12-9-386 and 2.6.12-10-386. I ran uname-r and found out that I was running kernel 2.6.12-9-386. So during the installation, the setup created 2.6.12-10-386 folder.Then I went back to the manual and the person was using 2.6.10-386. So I don't know what to do now? Anyone plz help, I have been tinkering with this network for about 6 hours with no luck. I would appreciate if someone helps. Thanks.

---

