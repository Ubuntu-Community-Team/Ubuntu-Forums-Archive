---
title: "Realtek RTL8723AE Wireless"
date: 2012-11-20
forum: Networking &amp; Wireless
---

### Post by Aessah on 2012-11-20
Hey guys, 

I'm new to Ubuntu 12.10; as a long time Windows user I welcomed a change however I am currently unable to connect to the internet. Under the network devices area the "No network devices available" message appears. I am unable to connect to the internet via ethernet as I am solely reliant upon wi-fi. As the title suggest my Wireless LAN is the Realtek RTL8723AE. Please help :confused:

---

### Post by ahallubuntu on 2012-11-20
This link might help: it provides a driver for that card that supposedly works if you build it:

[http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized](http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized)

---

### Post by Aessah on 2012-11-20
I'll give that a go and report back.

---

### Post by Aessah on 2012-11-20
So I signed in as the "root user" extracted the driver to the desktop and preformed the following: 

[LIST=1]
[*]Changed directory to the desktop.
[*]Changed directory to the extracted folder
[*]Typed "sudo make install"
[/LIST]

I then received the following error:

> make -C /lib/modules/3.5.0-17-generic/build M=/root/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012 modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-17-generic'
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.o
/root/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c: In function ‘_rtl_init_mac80211’:
/root/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:320:6: error: ‘IEEE80211_HW_BEACON_FILTER’ undeclared (first use in this function)
/root/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:320:6: note: each undeclared identifier is reported only once for each function it appears in
make[2]: *** [/root/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.o] Error 1
make[1]: *** [_module_/root/Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-17-generic'
make: *** [all] Error 2

---

### Post by Aessah on 2012-11-23
Any help would be appreciated.

---

### Post by potgieta on 2013-04-22
Searched several forums but this one worked for me as I had errors with the make part in other forums. Here a part needs to be commented out on base.c, I just deleted part and it worked for me. [http://mlkushan.blogspot.com/2012/10/ub ... s-not.html]("http://mlkushan.blogspot.com/2012/10/ubuntu-1204-wifi-network-was-not.html")

---

