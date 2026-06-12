---
title: "atheros and Ubuntu 8.10"
date: 2008-12-05
forum: Networking &amp; Wireless
---

### Post by spraveenitpro on 2008-12-05
Hi 

I use compaq c768TU laptop with atheros wifi chipset, now when I upgraded from 8.04 to 8.10 , the wifi broke and now when I try to compile madwifi , I get the following error :

> praveen@praveen-laptop:~/Desktop/madwifi-0.9.4$ sudo make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.27-9-generic/build SUBDIRS=/home/praveen/Desktop/madwifi-0.9.4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /home/praveen/Desktop/madwifi-0.9.4/net80211/ieee80211_power.o
/home/praveen/Desktop/madwifi-0.9.4/net80211/ieee80211_power.c: In function 'ieee80211_pwrsave':
/home/praveen/Desktop/madwifi-0.9.4/net80211/ieee80211_power.c:240: error: implicit declaration of function '__skb_append'
make[3]: *** [/home/praveen/Desktop/madwifi-0.9.4/net80211/ieee80211_power.o] Error 1
make[2]: *** [/home/praveen/Desktop/madwifi-0.9.4/net80211] Error 2
make[1]: *** [_module_/home/praveen/Desktop/madwifi-0.9.4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [modules] Error 2
praveen@praveen-laptop:~/Desktop/madwifi-0.9.4$ 

Please let me know what to do , I have already installed build-essentials.

Praveen

---

### Post by abhilashkumar on 2008-12-08
I too have an atheros wifi chip. My wifi didnt break on upgrade to 8.10.

However a few days later I did a full format and then a fresh 8.10 install. The wifi didnt work. I am using madwifi now (on 8.04 it worked with ndiswrapper). The wifi light doesnt work but its okay. [I used the instructions here]("http://ubuntuforums.org/showthread.php?t=1005138&highlight=madwifi")

[This one]("http://ubuntu-utah.ubuntuforums.org/showpost.php?p=5711824&postcount=6") is more detailed.

---

### Post by Casper Hansen on 2008-12-08
My friend has a Toshiba A110 Sattelite and his Atheros works. You have to install the backports, update hardware drivers and install the 5-something driver. Can't find the howto right now, but it's something like that^

---

