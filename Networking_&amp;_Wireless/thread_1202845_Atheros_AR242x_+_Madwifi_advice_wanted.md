---
title: "Atheros AR242x + Madwifi advice wanted"
date: 2009-07-02
forum: Networking &amp; Wireless
---

### Post by jadedcritic on 2009-07-02
Hello!  I give up, I've been making myself trying crazy trying to figure out how this works and not making much headway, so I thought I'd ask for some advice.

My laptop is using the following device:

03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

lsmod | grep -i ath
ath5k                 107008  0 
mac80211              217464  1 ath5k
led_class              12036  1 ath5k
cfg80211               38288  2 ath5k,mac80211

[   32.864896] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)

I'm getting SOME wireless connectivity, but the results are somewhat sporadic and unpredicatable, so I've been trying to figure out if there's a better way.

In my travels I've discovered ndiswrapper, if only to discover that there isn't a tested good windows driver for this chip:
[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Category:WORKS](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Category:WORKS)

I've also discovered numerous threads pointing the in the general direction of the madwifi driver.  
[http://madwifi-project.org](http://madwifi-project.org)

Some people say it works, some people say it doesn't work, some people say it needs a patch, and the patch link is dead.  By following various guides on and or linked to ubuntu forums, I've managed to download and install the necessary files, or so I thought.  I then blacklist the default drivers in etc/modprobe.d, and reboot.  After activating the madwifi driver in system/administration/hardware drivers, my networking shortcut in the upper right corner next to the speaker and date, simply greys out.  When I do an ifconfig I see no wlan entry.

I've got to be overlooking something, but I have no idea what it could be!
Any advice would be appreciated.

Edited: (Maybe this is part of it?)  I'm getting this output when I try 'sudo make install'

sudo make install
sh scripts/find-madwifi-modules.sh 2.6.28-13-generic 

WARNING:
It seems that there are modules left from previous MadWifi installations.
If you are unistalling the MadWifi modules please press "r" to remove them.
If you are installing new MadWifi modules, you should consider removing those
already installed, or else you may experience problems during operation.
Remove old modules?

[l]ist, [r]emove, [i]gnore or e[x]it (l,r,i,[x]) ? r
for i in ath/ ath_hal/ ath_rate/ net80211/; do \
		make -C $i install || exit 1; \
	done
make[1]: Entering directory `/usr/src/madwifi-0.9.4/ath'
test -d //lib/modules/2.6.28-13-generic/net || mkdir -p //lib/modules/2.6.28-13-generic/net
install ath_pci.ko //lib/modules/2.6.28-13-generic/net
install: cannot stat `ath_pci.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/usr/src/madwifi-0.9.4/ath'
make: *** [install-modules] Error 1

---

### Post by jorval on 2009-07-05
Hi Jadedcritic, in this link you can find de solution to your problem

[http://chamangt.wordpress.com/2008/05/08/activar-wireless-atheros-en-ubuntu-con-madwifi/]("http://chamangt.wordpress.com/2008/05/08/activar-wireless-atheros-en-ubuntu-con-madwifi/")

The page is in spanish but probably you can translate it. Regards.

---

