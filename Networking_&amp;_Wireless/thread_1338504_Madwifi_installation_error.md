---
title: "Madwifi installation error"
date: 2009-11-26
forum: Networking &amp; Wireless
---

### Post by nickda_corfu on 2009-11-26
Hi,i am trying to install the madwifi driver for my wireless card, but when doing the 'make command ' i get an error,
 here is what i have done and the error 

nikos@nickda:/usr/src/madwifi-0.9.4/scripts$ sudo ./madwifi-unload.bash
nikos@nickda:/usr/src/madwifi-0.9.4/scripts$ sudo ./find-madwifi-modules.sh $(uname -r)
nikos@nickda:/usr/src/madwifi-0.9.4/scripts$ cd ..
nikos@nickda:/usr/src/madwifi-0.9.4$ sudo make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.28-11-generic/build SUBDIRS=/usr/src/madwifi-0.9.4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /usr/src/madwifi-0.9.4/ath/if_ath.o
  CC [M]  /usr/src/madwifi-0.9.4/ath/if_ath_pci.o
  LD [M]  /usr/src/madwifi-0.9.4/ath/ath_pci.o
  CC [M]  /usr/src/madwifi-0.9.4/ath_hal/ah_os.o
  HOSTCC  /usr/src/madwifi-0.9.4/ath_hal/uudecode
  UUDECODE /usr/src/madwifi-0.9.4/ath_hal/i386-elf.hal.o
  LD [M]  /usr/src/madwifi-0.9.4/ath_hal/ath_hal.o
  CC [M]  /usr/src/madwifi-0.9.4/ath_rate/amrr/amrr.o
  LD [M]  /usr/src/madwifi-0.9.4/ath_rate/amrr/ath_rate_amrr.o
  CC [M]  /usr/src/madwifi-0.9.4/ath_rate/minstrel/minstrel.o
  LD [M]  /usr/src/madwifi-0.9.4/ath_rate/minstrel/ath_rate_minstrel.o
  CC [M]  /usr/src/madwifi-0.9.4/ath_rate/onoe/onoe.o
  LD [M]  /usr/src/madwifi-0.9.4/ath_rate/onoe/ath_rate_onoe.o
  CC [M]  /usr/src/madwifi-0.9.4/ath_rate/sample/sample.o
  LD [M]  /usr/src/madwifi-0.9.4/ath_rate/sample/ath_rate_sample.o
  CC [M]  /usr/src/madwifi-0.9.4/net80211/if_media.o
  CC [M]  /usr/src/madwifi-0.9.4/net80211/ieee80211.o
  CC [M]  /usr/src/madwifi-0.9.4/net80211/ieee80211_beacon.o
  CC [M]  /usr/src/madwifi-0.9.4/net80211/ieee80211_crypto.o
  CC [M]  /usr/src/madwifi-0.9.4/net80211/ieee80211_crypto_none.o
  CC [M]  /usr/src/madwifi-0.9.4/net80211/ieee80211_input.o
  CC [M]  /usr/src/madwifi-0.9.4/net80211/ieee80211_node.o
  CC [M]  /usr/src/madwifi-0.9.4/net80211/ieee80211_output.o
  CC [M]  /usr/src/madwifi-0.9.4/net80211/ieee80211_power.o
/usr/src/madwifi-0.9.4/net80211/ieee80211_power.c: In function 'ieee80211_pwrsave':
/usr/src/madwifi-0.9.4/net80211/ieee80211_power.c:240: error: implicit declaration of function '__skb_append'
make[3]: *** [/usr/src/madwifi-0.9.4/net80211/ieee80211_power.o] Error 1
make[2]: *** [/usr/src/madwifi-0.9.4/net80211] Error 2
make[1]: *** [_module_/usr/src/madwifi-0.9.4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [modules] Error 2


i have tried to find the solution on google but the only pages that come up with the same error are in spanish(and i dont know it) . can anyone help??

---

### Post by drpjkurian on 2009-11-27
> **nickda_corfu said:**
> Hi,i am trying to install the madwifi driver for my wireless card, but when doing the 'make command ' i get an error,
 here is what i have done and the error 

nikos@nickda:/usr/src/madwifi-0.9.4/scripts$ sudo ./madwifi-unload.bash
nikos@nickda:/usr/src/madwifi-0.9.4/scripts$ sudo ./find-madwifi-modules.sh $(uname -r)
nikos@nickda:/usr/src/madwifi-0.9.4/scripts$ cd ..
nikos@nickda:/usr/src/madwifi-0.9.4$ sudo make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.28-11-generic/build SUBDIRS=/usr/src/madwifi-0.9.4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /usr/src/madwifi-0.9.4/ath/if_ath.o
  CC [M]  /usr/src/madwifi-0.9.4/ath/if_ath_pci.o
  LD [M]  /usr/src/madwifi-0.9.4/ath/ath_pci.o
  CC [M]  /usr/src/madwifi-0.9.4/ath_hal/ah_os.o
  HOSTCC  /usr/src/madwifi-0.9.4/ath_hal/uudecode
  UUDECODE /usr/src/madwifi-0.9.4/ath_hal/i386-elf.hal.o
  LD [M]  /usr/src/madwifi-0.9.4/ath_hal/ath_hal.o
  CC [M]  /usr/src/madwifi-0.9.4/ath_rate/amrr/amrr.o
  LD [M]  /usr/src/madwifi-0.9.4/ath_rate/amrr/ath_rate_amrr.o
  CC [M]  /usr/src/madwifi-0.9.4/ath_rate/minstrel/minstrel.o
  LD [M]  /usr/src/madwifi-0.9.4/ath_rate/minstrel/ath_rate_minstrel.o
  CC [M]  /usr/src/madwifi-0.9.4/ath_rate/onoe/onoe.o
  LD [M]  /usr/src/madwifi-0.9.4/ath_rate/onoe/ath_rate_onoe.o
  CC [M]  /usr/src/madwifi-0.9.4/ath_rate/sample/sample.o
  LD [M]  /usr/src/madwifi-0.9.4/ath_rate/sample/ath_rate_sample.o
  CC [M]  /usr/src/madwifi-0.9.4/net80211/if_media.o
  CC [M]  /usr/src/madwifi-0.9.4/net80211/ieee80211.o
  CC [M]  /usr/src/madwifi-0.9.4/net80211/ieee80211_beacon.o
  CC [M]  /usr/src/madwifi-0.9.4/net80211/ieee80211_crypto.o
  CC [M]  /usr/src/madwifi-0.9.4/net80211/ieee80211_crypto_none.o
  CC [M]  /usr/src/madwifi-0.9.4/net80211/ieee80211_input.o
  CC [M]  /usr/src/madwifi-0.9.4/net80211/ieee80211_node.o
  CC [M]  /usr/src/madwifi-0.9.4/net80211/ieee80211_output.o
  CC [M]  /usr/src/madwifi-0.9.4/net80211/ieee80211_power.o
/usr/src/madwifi-0.9.4/net80211/ieee80211_power.c: In function 'ieee80211_pwrsave':
/usr/src/madwifi-0.9.4/net80211/ieee80211_power.c:240: error: implicit declaration of function '__skb_append'
make[3]: *** [/usr/src/madwifi-0.9.4/net80211/ieee80211_power.o] Error 1
make[2]: *** [/usr/src/madwifi-0.9.4/net80211] Error 2
make[1]: *** [_module_/usr/src/madwifi-0.9.4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [modules] Error 2


i have tried to find the solution on google but the only pages that come up with the same error are in spanish(and i dont know it) . can anyone help??

Hi
Please visit my thread to install Madwifi drivers for your Atheros card
[http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)

With regards
Dr Kurian

---

### Post by nickda_corfu on 2009-11-29
thanks mate,the best article ever!!

---

### Post by pvossen on 2009-11-29
> **drpjkurian said:**
> Hi
Please visit my thread to install Madwifi drivers for your Atheros card
[http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)

With regards
Dr Kurian

Have been trying for three days to get this card operational.
I've installed a couple of one's before with Ubuntu with
the old windows driver disks. However, I'm using a generic
linux one for an Atheros Ar 5100 for a customer of mine with
Ubuntu Moblin Remix 9.10. Its my first experience with
Remix, it looks good, but I have tried you idea for installation
of an Atheros card and another script. So far nothing. Now it
does recognize the driver in Hardware. It just doesn't do 
anything. Now I haven't tried wicd yet, but I've never used
it before.

Can't wait till we become more mobile friendly with our
Linux systems. If we were I'd hardly ever have to sell
a Windows machine.

Patrick


PS In multicast it lists some activity in the loopless
tab, but nothing resonates to actual activity for
firefox to run.

---

### Post by drpjkurian on 2009-11-30
> **pvossen said:**
> Have been trying for three days to get this card operational.
I've installed a couple of one's before with Ubuntu with
the old windows driver disks. However, I'm using a generic
linux one for an Atheros Ar 5100 for a customer of mine with
Ubuntu Moblin Remix 9.10. Its my first experience with
Remix, it looks good, but I have tried you idea for installation
of an Atheros card and another script. So far nothing. Now it
does recognize the driver in Hardware. It just doesn't do 
anything. Now I haven't tried wicd yet, but I've never used
it before.

Can't wait till we become more mobile friendly with our
Linux systems. If we were I'd hardly ever have to sell
a Windows machine.


Patrick


PS In multicast it lists some activity in the loopless
tab, but nothing resonates to actual activity for
firefox to run.

Hi

I am very sorry to hear that your wireless is not working. I presume that the instructions which was mentioned in  thread may not apply for Moblin release. please streamline your search sich as Atheros and Moblin

With regards
Dr Kurian

---

### Post by drpjkurian on 2009-11-30
> **nickda_corfu said:**
> thanks mate,the best article ever!!

Hi Nickda
Thank you for your compliments.

Dr Kurian

---

