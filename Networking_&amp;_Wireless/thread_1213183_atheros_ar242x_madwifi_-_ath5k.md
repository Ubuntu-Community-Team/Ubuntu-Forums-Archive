---
title: "atheros ar242x madwifi - ath5k"
date: 2009-07-14
forum: Networking &amp; Wireless
---

### Post by maestrobwh1 on 2009-07-14
The ath5k that ships with jaunty gives a very unreliable performance with my wireless card in my eee-pc 701.  I blacklisted it and compiled madwifi-trunk and did the usual make, make install, etc.  It works but is worse than ath5k.  I uninstalled it, rebooted and tried madwifi-hal latest, and it was not much better (drops connection, 50% 5 feet from router, choppy internet performance, etc).  I am using ndiswrapper right now, and it works well enough except when it detaches from a weaker signal, it won't reconnect unless I reboot.  There are also issues with it coming back on if I use the wifi toggle.  

On the same PC, I also have Arch kernel 2.6.28 installed.  I used the same exact madwifi-hal tarball, compiled it and installed it, and I have theh BEST performance from my wireless card (was using ndiswrapper for a while).

**What is preventing madwifi from working well in Ubuntu?**  Ath5k is NOT loaded.

---

### Post by Crafty Kisses on 2009-07-14
I have the exact same Eee PC as you. First what you want to do is run the following:
```
ndiswrapper -e (drivername)
```
That will remove the ndiswrapper driver, then I suggest you download this **[driver]("http://file-hosting.site-hosts.net/eeepc/madwifi-nr-r3366+ar5007.tar.gz")**. Once you have grabbed that driver, you need to make sure you have a couple of packages installed, so grab build-essential, you can do this by running as root:
```
apt-get install build-essential
```
Then you have the proper tools to compile, so now extract the driver by running:
```
tar xzf madwifi-nr-(drivername).tar.gz
```
Once you have extracted the file, you need to go into the folder by running:
```
cd madwifi-nr-(drivername)/
```
Once your in the directory, you now need to run:
```
make
make install
```
Once you have done that, you can reboot by running:
```
shutdown -r now
```
Once the reboot is complete you should have way better working wireless.

---

### Post by maestrobwh1 on 2009-07-14
Thanks for the quick reply.  I get some build activity and it errors out with

/media/STORAGE/madwifi-ng-r3366+ar5007/net80211/ieee80211_power.c: In function 'ieee80211_pwrsave':
/media/STORAGE/madwifi-ng-r3366+ar5007/net80211/ieee80211_power.c:246: **error: implicit declaration of function '__skb_append'**
make[3]: *** [/media/STORAGE/madwifi-ng-r3366+ar5007/net80211/ieee80211_power.o] Error 1
make[2]: *** [/media/STORAGE/madwifi-ng-r3366+ar5007/net80211] Error 2
make[1]: *** [_module_/media/STORAGE/madwifi-ng-r3366+ar5007] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.28-ARCH'
make: *** [modules] Error 2


I googled this and it tells me I need a later build?  It is actually defunct on madwifi's site so I don't think there is a later build.  Using kernel 2,6,28

---

### Post by ubunny on 2009-07-14
don't know if it's applicable for you, but here's a blog entry regarding ar242x and madwifi.  the comments are particularly useful and active.

[http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/](http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/)

---

