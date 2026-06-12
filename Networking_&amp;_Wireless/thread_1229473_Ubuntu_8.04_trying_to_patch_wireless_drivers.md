---
title: "Ubuntu 8.04 trying to patch wireless drivers"
date: 2009-08-02
forum: Networking &amp; Wireless
---

### Post by learner3 on 2009-08-02
Hello all,

I have made this thread because I am stuck on getting my wireless card to packet injection mode on Ubuntu. I have followed many documentations and tutorials over the week and have not found a solution so far.
so I post here for some advice.

I am able to run airoman-ng and put it in mon0 which is monitor mode, I am able to run airodump-ng to start capturing packets, I am able to run kismet to see what networks bssid but this is the part I am stuck at airoplay-ng the packet injection part.


I have 

Asus Laptop M50series

Ubuntu 8:04
Intel 4965 wireless A,G,N

  Kernel 2.6.27.14
  Kernel headers
  Kernel sources
compat-wireless-2.6
Basic Development( make,Gcc,Zsgznc)
Mac80211 Installed
iwlwifi-4965-ucode-228.61.2.24

I also did this to get the programs in ubuntu 8.04

sudo apt-get install build-essential
sudo apt-get install aircrack
sudo apt-get install kismet
sudo apt-get install airsnort
sudo apt-get install linux-source
sudo apt-get install linux-headers
sudo apt-get install sharutils

I use modprobe

Modprobe Mac80211 

No errors or feedback


Modprobe iwlwifi-4965-ucode-228.61.2.24

No errors or feedback

I have went to [www.intellinuxwireless.org]("http://www.intellinuxwireless.org") and read/use they patches.

Downloaded

iwlwifi-4965-ucode-228.61.2.24.tgz

Successful, Installed it 

This is the part I am worried about, I tried to install mac80211-10.0.4.tgz  which my kernal is more newer but I believe it failed by this input error

make: *** [compatible/Mofified] Error 1
mac80211-10.0.4.tgz

I did have a lot of issues installing mac80211 but at the end did it. by using this tutiorial and the newer proper patch I am suppose to use.



[http://www.aircrack-ng.org/doku.php?id=iwlagn&DokuWiki=d3a71e72bfbba73ba53418fef5b87bd2](http://www.aircrack-ng.org/doku.php?id=iwlagn&DokuWiki=d3a71e72bfbba73ba53418fef5b87bd2)


cd ~
 tar xjf compat-wireless-2.6.tar.bz2
 cd compat-wireless-2009-*
 wget [http://patches.aircrack-ng.org/mac80211_2.6.28-rc4-wl_frag+ack_v3.patch](http://patches.aircrack-ng.org/mac80211_2.6.28-rc4-wl_frag+ack_v3.patch)
 patch -p1 < mac80211_2.6.28-rc4-wl_frag+ack_v3.patch
 wget [http://patches.aircrack-ng.org/mac80211-2.6.29-fix-tx-ctl-no-ack-retry-count.patch](http://patches.aircrack-ng.org/mac80211-2.6.29-fix-tx-ctl-no-ack-retry-count.patch)
 patch -p1 < mac80211-2.6.29-fix-tx-ctl-no-ack-retry-count.patch
 make -j4
 make unload [as root!]
 make install [as root!]
 echo options iwlagn swcrypto=1 >> /etc/modprobe.d/options [as root!]
 make load [as root!]


But I still further have issues with this.

I test if the packet injection works by using

Sudo aireplay -9 mon0

I get no AP
No answer

---

