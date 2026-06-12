---
title: "Setting up Intel Pro 3945ABG for aircrack"
date: 2011-02-22
forum: Networking &amp; Wireless
---

### Post by layers on 2011-02-22
I've always wanted to learn this branch of computing, and I do think it's rather interesting. So, I was following in unison both [this]("http://www.aircrack-ng.org/doku.php?id=ipw3945&DokuWiki=8dc98f84f702566e402602aa71dfaaf9") and [this]("http://maxi-pedia.com/how+to+crack+WEP+with+intel+PRO+wireless+3945ABG"), which so far just tell me to download ipwraw-ng and extract it, but when I cd into the folder, and say make, I get this:```
ibo@ibo-laptop:~$ cd Desktop/ipwraw-ng/
ibo@ibo-laptop:~/Desktop/ipwraw-ng$ make

WARNING: $SHELL not set to bash.
If you experience build errors, try
'make SHELL=/bin/bash'.

make -C /lib/modules/2.6.32-28-generic/build M=/home/ibo/Desktop/ipwraw-ng modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-28-generic'

WARNING: $SHELL not set to bash.
If you experience build errors, try
'make SHELL=/bin/bash'.

  CC [M]  /home/ibo/Desktop/ipwraw-ng/ipwraw.o
/home/ibo/Desktop/ipwraw-ng/ipwraw.c:43:27: error: net/ieee80211.h: No such file or directory
In file included from /home/ibo/Desktop/ipwraw-ng/ipwraw.h:51,
                 from /home/ibo/Desktop/ipwraw-ng/ipwraw.c:48:
/home/ibo/Desktop/ipwraw-ng/iwlwifi_hw.h:525: error: array type has incomplete element type
/home/ibo/Desktop/ipwraw-ng/iwlwifi_hw.h:847: error: array type has incomplete element type
In file included from /home/ibo/Desktop/ipwraw-ng/ipwraw.c:48:
LOTS OF ERRORS
/home/ibo/Desktop/ipwraw-ng/ipwraw.c:8902: error: ‘ARPHRD_IEEE80211’ undeclared (first use in this function)
make[2]: *** [/home/ibo/Desktop/ipwraw-ng/ipwraw.o] Error 1
make[1]: *** [_module_/home/ibo/Desktop/ipwraw-ng] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-28-generic'
make: *** [modules] Error 2
ibo@ibo-laptop:~/Desktop/ipwraw-ng$ 

```

I tried following other threads about this, but they are all rather generic in their speaking manner, and not quite specific to my case. Can anyone help me install it?

---

### Post by howefield on 2011-02-23
Moved to "*Networking & Wireless*" where you are likely to get better help for your query than you would in Tutorials & Tips.

---

### Post by layers on 2011-02-23
I had the wrong headers, thanks.

---

### Post by layers on 2011-02-25
Except I get this:
```

wlan0     IEEE 802.11abg  Mode:Monitor  Frequency:2.457 GHz  Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
ibo@ibo-laptop:~$ sudo aireplay-ng -9 -e 1130 -a 00:21:91:07:AA:87 wlan0
21:57:54  Waiting for beacon frame (BSSID: 00:21:91:07:AA:87) on channel 10
21:57:54  Trying broadcast probe requests...
21:57:56  No Answer...
21:57:56  Found 1 AP 

21:57:56  Trying directed probe requests...
21:57:56  00:21:91:07:AA:87 - channel: 10 - '1130'
21:58:02   0/30:   0%

ibo@ibo-laptop:~$
```Does that mean injection isn't working properly? Or at all? I'm confused, how am I supposed to change that?

---

