---
title: "Madwifi drives me mad :)"
date: 2008-12-04
forum: Networking &amp; Wireless
---

### Post by damu on 2008-12-04
Hi,

I have updated Ubuntu to 8.10 on the lappy (Fujitsu - Amilo Pi2512) of my partner as we needed some functionnalities only available on 8.10

For 8.04, I managed to get the atheros chipset working using madwifi.

I read somewhere that it wasn't needed in 8.10. It was just a matter of getting the latest atheros drivers and enabling them in "proprietary drivers"...it din't work for me.

So back to the madwifi road. So far I have :
- removed previous installation by following the script in the How-to on the madwifi website
- installed the required linux headers before installing madwifi 
-tried to install 2 different madwifi drivers:
 . the one that I has been working on 8.04 
 . the latest madwifi (0.9.4) 

...to no avail- In both cases I have errors when I do "make" (see the part in bold of the following quote): 

> maggie@maggie-laptop:~$ sudo  ifconfig eth0 down
maggie@maggie-laptop:~$ cd /home/maggie/tech/madwifi/madwifi-0.9.4
maggie@maggie-laptop:~/tech/madwifi/madwifi-0.9.4$ sudo make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.27-9-generic/build SUBDIRS=/home/maggie/tech/madwifi/madwifi-0.9.4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /home/maggie/tech/madwifi/madwifi-0.9.4/ath/if_ath.o
  CC [M]  /home/maggie/tech/madwifi/madwifi-0.9.4/ath/if_ath_pci.o
  LD [M]  /home/maggie/tech/madwifi/madwifi-0.9.4/ath/ath_pci.o
  CC [M]  /home/maggie/tech/madwifi/madwifi-0.9.4/ath_hal/ah_os.o
  HOSTCC  /home/maggie/tech/madwifi/madwifi-0.9.4/ath_hal/uudecode
  UUDECODE /home/maggie/tech/madwifi/madwifi-0.9.4/ath_hal/i386-elf.hal.o
  LD [M]  /home/maggie/tech/madwifi/madwifi-0.9.4/ath_hal/ath_hal.o
  CC [M]  /home/maggie/tech/madwifi/madwifi-0.9.4/ath_rate/amrr/amrr.o
  LD [M]  /home/maggie/tech/madwifi/madwifi-0.9.4/ath_rate/amrr/ath_rate_amrr.o
  CC [M]  /home/maggie/tech/madwifi/madwifi-0.9.4/ath_rate/minstrel/minstrel.o
  LD [M]  /home/maggie/tech/madwifi/madwifi-0.9.4/ath_rate/minstrel/ath_rate_minstrel.o
  CC [M]  /home/maggie/tech/madwifi/madwifi-0.9.4/ath_rate/onoe/onoe.o
  LD [M]  /home/maggie/tech/madwifi/madwifi-0.9.4/ath_rate/onoe/ath_rate_onoe.o
  CC [M]  /home/maggie/tech/madwifi/madwifi-0.9.4/ath_rate/sample/sample.o
  LD [M]  /home/maggie/tech/madwifi/madwifi-0.9.4/ath_rate/sample/ath_rate_sample.o
  CC [M]  /home/maggie/tech/madwifi/madwifi-0.9.4/net80211/if_media.o
  CC [M]  /home/maggie/tech/madwifi/madwifi-0.9.4/net80211/ieee80211.o
  CC [M]  /home/maggie/tech/madwifi/madwifi-0.9.4/net80211/ieee80211_beacon.o
  CC [M]  /home/maggie/tech/madwifi/madwifi-0.9.4/net80211/ieee80211_crypto.o
  CC [M]  /home/maggie/tech/madwifi/madwifi-0.9.4/net80211/ieee80211_crypto_none.o
  CC [M]  /home/maggie/tech/madwifi/madwifi-0.9.4/net80211/ieee80211_input.o
  CC [M]  /home/maggie/tech/madwifi/madwifi-0.9.4/net80211/ieee80211_node.o
  CC [M]  /home/maggie/tech/madwifi/madwifi-0.9.4/net80211/ieee80211_output.o
  CC [M]  /home/maggie/tech/madwifi/madwifi-0.9.4/net80211/ieee80211_power.o
/home/maggie/tech/madwifi/madwifi-0.9.4/net80211/ieee80211_power.c: In function 'ieee80211_pwrsave':
/home/maggie/tech/madwifi/madwifi-0.9.4/net80211/ieee80211_power.c:240: error: implicit declaration of function '__skb_append'
**make[3]: *** [/home/maggie/tech/madwifi/madwifi-0.9.4/net80211/ieee80211_power.o] Error 1**
[B]make[2]: *** [/home/maggie/tech/madwifi/madwifi-0.9.4/net80211] Error 2
make[1]: *** [_module_/home/maggie/tech/madwifi/madwifi-0.9.4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [modules] Error 2[/B]
maggie@maggie-laptop:~/tech/madwifi/madwifi-0.9.4$ 

The problem is a bit overwhelming for me. Can anyone help?

Thanks

---

### Post by damu on 2008-12-04
anyone has a solution?

thanks

---

### Post by IQRules on 2008-12-04
Maybe you do not need madwifi. Do some googling, could be some tar files ready for you. What is lspci | grep -i networ

---

### Post by bsharp42 on 2008-12-04
That is the exact same error i get if i try to do the make from the mmadwifi tarball.

Any help would be appreciated

---

### Post by kevdog on 2008-12-04
did you try the svn or 0.9.3 release?

---

