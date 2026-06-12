---
title: "Madwifi make error."
date: 2009-07-20
forum: Networking &amp; Wireless
---

### Post by spacefreak on 2009-07-20
So, I've been trying to get my wireless card working for a bit now. I'm not able to hard connect, so it's a bit more complicated. I'm running a Thinkpad X200 Tablet, and I finally ran across a thread where several people claimed madwifi was the ticket. (ndisgtk had some issues.) I installed build essential from the cd, and when I went to make madwifi I got this:

make -C /lib/modules/2.6.28-11-generic/build SUBDIRS=/home/ezra/Desktop/madwifi-0.9.4 modules 
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic' 
  CC [M]  /home/ezra/Desktop/madwifi-0.9.4/net80211/ieee80211_power.o 
/home/ezra/Desktop/madwifi-0.9.4/net80211/ieee80211_power.c: In function 'ieee80211_pwrsave': 
/home/ezra/Desktop/madwifi-0.9.4/net80211/ieee80211_power.c:240: error: implicit declaration of function '__skb_append' 
make[3]: *** [/home/ezra/Desktop/madwifi-0.9.4/net80211/ieee80211_power.o] Error 1 
make[2]: *** [/home/ezra/Desktop/madwifi-0.9.4/net80211] Error 2 
make[1]: *** [_module_/home/ezra/Desktop/madwifi-0.9.4] Error 2 
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic' 
make: *** [modules] Error 2 

I'm not exactly sure why, but I've never really been able to use the make command with any consistency in Ubuntu. I have with other distros, but I think Ubuntu dislikes me. Any ideas on how I clear this up?

---

### Post by t0mppa on 2009-07-21
A little Googling shows multiple tickets about this in Madwifi's bug tracker. It's been fixed in the later versions though, so just grabbing an up to date build from [here]("http://snapshots.madwifi-project.org/") should solve the issue.

Personally I used the *hal-10.5.6-current* build on Ibex, but since ath5k works just fine with Jaunty on my card, haven't built Madwifi drivers since the upgrade. Anyhow, with the merge of the free & trunk branches, I guess the trunk one is recommended now, as it doesn't depend on the binary-only Hardware Abstraction Layer.

---

