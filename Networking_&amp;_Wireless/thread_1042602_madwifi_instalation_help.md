---
title: "madwifi instalation help"
date: 2009-01-17
forum: Networking &amp; Wireless
---

### Post by pretobomba on 2009-01-17
so i'm running on kubuntu 8.10 ,
$ uname -r
2.6.27-7-generic
and when i type make into the madwifi directory i get the following error
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/home/pretobomba/madwifi-0.9.4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /home/pretobomba/madwifi-0.9.4/net80211/ieee80211_power.o
/home/pretobomba/madwifi-0.9.4/net80211/ieee80211_power.c: In function 'ieee80211_pwrsave':
/home/pretobomba/madwifi-0.9.4/net80211/ieee80211_power.c:240: error: implicit declaration of function '__skb_append'
make[3]: *** [/home/pretobomba/madwifi-0.9.4/net80211/ieee80211_power.o] Error 1
make[2]: *** [/home/pretobomba/madwifi-0.9.4/net80211] Error 2
make[1]: *** [_module_/home/pretobomba/madwifi-0.9.4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [modules] Error 2
is there any thing that is missing for the instalation? any help would be apreciated.

---

### Post by 2hot6ft2 on 2009-01-17
> **pretobomba said:**
> 
  CC [M]  /home/pretobomba/madwifi-0.9.4/net80211/[COLOR="Blue"]ieee80211[/COLOR]_power.o
/home/pretobomba/madwifi-0.9.4/net80211/[COLOR="Blue"]ieee80211[/COLOR]_power.c: In function '[COLOR="Blue"]ieee80211[/COLOR]_pwrsave':
/home/pretobomba/madwifi-0.9.4/net80211/ieee80211_power.c:240: error: implicit declaration of function '__skb_append'
make[3]: *** [/home/pretobomba/madwifi-0.9.4/net80211/[COLOR="Blue"]ieee80211[/COLOR]_power.o] Error 1
make[2]: *** [/home/pretobomba/madwifi-0.9.4/net80211] Error 2
make[1]: *** [_module_/home/pretobomba/madwifi-0.9.4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [modules] Error 2
is there any thing that is missing for the instalation? any help would be apreciated.
This may or may not help. I believe that 8.10 uses mac80211 instead of ieee80211.
And that 8.10 comes with ath9k (at least mine did) and maybe even ath5k (I blacklisted it in favor of ath9k)
If I have the history right first came madwifi then ath5k and now it's up to ath9k. So I think you're taking a step backwards there.

I'm not real familiar with kubuntu, maybe this will help.
[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

Since there's nothing about your card or chipset there.
[http://wireless.kernel.org/en/users/Drivers/ath9k](http://wireless.kernel.org/en/users/Drivers/ath9k)

---

