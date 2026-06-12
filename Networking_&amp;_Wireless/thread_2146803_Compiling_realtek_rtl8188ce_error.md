---
title: "Compiling realtek rtl8188ce error"
date: 2013-05-19
forum: Networking &amp; Wireless
---

### Post by Slixt on 2013-05-19
Okay, so.. I've decided to try the realtek site's linux drivers for my internal wifi card since I upgraded to 13.04. I couldn't get the compile to work in the last version and figured it might now.. but, it does not. So, I'm hoping some of you can tell me what i'm doing wrong here. I've made myself root and cd into the top level of the extracted file as it tells me to and when I get to make, this happens.
```
root@comet:/home/fox/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013# make
make -C /lib/modules/3.8.0-22-generic/build M=/home/fox/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013 modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-22-generic'
  CC [M]  /home/fox/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.o
In file included from /home/fox/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c:39:0:
/home/fox/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/pci.h:247:15: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rtl_pci_probe’
make[2]: *** [/home/fox/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.o] Error 1
make[1]: *** [_module_/home/fox/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-22-generic'
make: *** [all] Error 2
root@comet:/home/fox/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013# 


```

It looks as if something is not correct with it but, i wouldn't know where to begin changing it. I could be just doing something wrong too perhaps.

---

### Post by Slixt on 2013-05-19
Okay, so I finally found this blog [http://www.perseosblog.com/en/posts/solving-connection-problem-with-realtek-wifi-card-rtl8188ce-rtl8192ce-rtl8191se-and-rtl8192de-on-debian-ubuntu-and-derivatives/](http://www.perseosblog.com/en/posts/solving-connection-problem-with-realtek-wifi-card-rtl8188ce-rtl8192ce-rtl8191se-and-rtl8192de-on-debian-ubuntu-and-derivatives/) which helped me with part of it, now I got this problem left. 

```
root@comet:/home/fox/realtek# make
make -C /lib/modules/3.8.0-22-generic/build M=/home/fox/realtek modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-22-generic'
  CC [M]  /home/fox/realtek/base.o
In file included from /home/fox/realtek/base.c:39:0:
/home/fox/realtek/pci.h:247:1: error: implicit declaration of function ‘rtl_pci_probe’ [-Werror=implicit-function-declaration]
/home/fox/realtek/pci.h:247:31: error: expected expression before ‘struct’
cc1: some warnings being treated as errors
make[2]: *** [/home/fox/realtek/base.o] Error 1
make[1]: *** [_module_/home/fox/realtek] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-22-generic'
make: *** [all] Error 2


```

---

### Post by Slixt on 2013-05-20
bumping this.. I still can't find the answer to it.

---

### Post by wormfl on 2013-05-21
I'm having exactly the same problem with compiling this driver. Maybe we're making both the same stupid error, or it's a coding issue.
Being a Linux starter (just for a week), I don't know if it's apropriate to change (fix ) the code inside.

What I've already found to get the code running further, is to delete in pci.c and pci.h the following statements:
```
__devinit
__devinitdata
```

Then I still got errors in /rtl8192ce/sw.c :
```

/home/filip/Downloads/realtek/rtl8192ce/sw.c:373:1: fout: expected ‘,’ or ‘;’ before ‘static’
/home/filip/Downloads/realtek/rtl8192ce/sw.c: In functie ‘rtl92ce_module_init’:
/home/filip/Downloads/realtek/rtl8192ce/sw.c:392:8: fout: ‘rtl92ce_driver’ undeclared (first use in this function)
/home/filip/Downloads/realtek/rtl8192ce/sw.c:392:8: note: each undeclared identifier is reported only once for each function it appears in
/home/filip/Downloads/realtek/rtl8192ce/sw.c: In functie ‘rtl92ce_module_exit’:
/home/filip/Downloads/realtek/rtl8192ce/sw.c:401:25: fout: ‘rtl92ce_driver’ undeclared (first use in this function)

```

Outprint of the EOF sw.c , starting from line 364:
[URL="http://pastebin.com/ueqjaCy1"]http://pastebin.com/ueqjaCy1dcc
[/URL]
No clue where to find these errors :-k

---

### Post by Comasci on 2013-05-25
I've been having the same problem, and I think I have a solution:

First, if you modified pci.h or any other file as per other suggestions, revert back to how it was originally.  Then add the following to the top of pci.h (or it can be added just below the initial commenting):

```

#ifndef __devinit
#define __devinit
#define __devinitdata
#endif

```

If you haven't already, make sure gcc and build-essential are installed:

```
sudo apt-get install gcc build-essential
```

Now, switch to the directory where you extracted the driver files, and:

```

sudo su
make clean
make
make install

```

This fixed the compilation errors for me.  After rebooting, things seem to be working so far.  But my problem has been intermittent, so we'll see.

Background: After googling "__devinit", it appears **__devinit** and** __devinitdata** were macros that were defined in the linux kernel, and have been removed in a recent build.  This appears to be affecting several drivers.  They seem to no longer be needed, and therefore defining these as empty strings appears to be safe.

---

### Post by varunendra on 2013-05-26
> **Comasci said:**
> They seem to no longer be needed, and **therefore defining these as empty strings appears to be safe**.

That, if true, is a very useful information Comasci, thank you! I was myself looking for a workaround to this compiling error and was hesitating to include or remove these error related parts for the same reason (safe or not?).

Can you recall and share with us the source of this info please? I found the part about removing "system/asm.h" in the kernel git-hub, but couldn't find anything related to this one.

---

### Post by wormfl on 2013-05-26
> **Comasci said:**
> 
```

#ifndef __devinit
#define __devinit
#define __devinitdata
#endif

```


Nice fix, this one solved the compiling headaches :)

I experience the signal strength has increased, now I hope it will run stable.

---

### Post by Comasci on 2013-05-27
> **varunendra said:**
> Can you recall and share with us the source of this info please? I found the part about removing "system/asm.h" in the kernel git-hub, but couldn't find anything related to this one.

I made the assumption based on the fact that it seemed to work [here]("http://sourceforge.net/apps/trac/dvbhdhomerun/ticket/18") and [here]("http://lists.xen.org/archives/html/xen-devel/2013-02/msg00735.html").  It made me confident enough to give it a shot!  Still seems to be working for me.

---

### Post by varunendra on 2013-05-27
> **Comasci said:**
> I made the assumption based on the fact that it seemed to work [here]("http://sourceforge.net/apps/trac/dvbhdhomerun/ticket/18") and [here]("http://lists.xen.org/archives/html/xen-devel/2013-02/msg00735.html").  It made me confident enough to give it a shot!  Still seems to be working for me.

Well, good enough for me as long as it works :)

---

### Post by o----o on 2013-07-07
Grate
The installation went ok, finally :)
Lenovo L530, Linux 2046 3.8.3-030803-generic, x86_64 x86_64 x86_64 GNU/Linux

---

### Post by Jacob_Sherven on 2013-09-16
Awesome work! Worked for me as well here.

---

### Post by sidney-harrell on 2014-08-10
Apparently Freedom Ben is better at supporting Realtek's crap than Realtek is. [http://askubuntu.com/questions/367587/unable-to-compile-realtek-rtl8188ce-driver-on-ubuntu-13-10/367588#367588](http://askubuntu.com/questions/367587/unable-to-compile-realtek-rtl8188ce-driver-on-ubuntu-13-10/367588#367588)
[https://github.com/FreedomBen/rtl8188ce-linux-driver](https://github.com/FreedomBen/rtl8188ce-linux-driver)
There are branches for different distributions.

---

