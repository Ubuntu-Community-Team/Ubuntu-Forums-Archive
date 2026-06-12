---
title: "Wireless connection problems with ath9k + hostapd"
date: 2010-02-20
forum: Networking &amp; Wireless
---

### Post by logiconcepts819 on 2010-02-20
Hello.  I have configured my TP-Link WN951N to operate in master mode by using the ath9k driver and hostapd.  I have also set up NAT forwarding.  However, I have run into a problem that I can't seem to solve.  Sometimes I have a connection to both the Internet and the network.  Sometimes I have no connection to the Internet, but I have a connection to the network.  However, most of the time, I have no connection to anything at all (i.e. the wireless works but there is no network connectivity).  I speculate that something is wrong with either the ath9k driver or hostapd, or else something is wrong with one or more of my configuration files.  I have even tried replacing NetworkManager with wicd, and that didn't help at all.  What can possibly be wrong here?  Attached is a gzip'd tarball containing some configuration files and logs inside their respective directories.

P.S.: I even tried the madwifi driver from SVN and, lo and behold, network connectivity between the server and the wireless client fails after a while even with the madwifi driver.  Is it possible that I'm in serious need of a different wireless card?  I have just inserted a gigabit Ethernet card into the server machine, bridged its interface together with the wireless interface, and connectivity via Ethernet works like a charm.  Why can't connectivity via wireless work like a charm?

---

### Post by logiconcepts819 on 2010-02-27
The problem only worsens after installing the latest [Linux wireless drivers]("http://wireless.kernel.org/en/users/Download#Directly_downloading_the_tarball") as described on [this site]("http://blog.bokhorst.biz/3395/computers-en-internet/asrock-ion-330ht-as-wireless-access-point/").  I am able to connect to the server machine fine via wireless.  However, after using the wireless connection to navigate to a few web pages for 30 seconds or so, the connection dies, and certain processes on the server machine (like sudo and firefox) freeze and become uninterruptible.  This mysterious failure also seems to freeze dnsmasq, since computers connected to the LAN interface lose network connectivity as well.  At this point, I'd have to force the machine off (using the power button) and on again in order to get everything working again.  I have examined the daemon.log, debug, dmesg, kern.log, messages, and syslog files under the /var/log directory, but I could not find any error messages related to this situation.

---

### Post by Greenwidth on 2010-02-27
Installing the backport modules helps some ppl using the ath9k driver:
linux-backports-modules-karmic-generic
linux-backports-modules-wireless-karmic-generic
(I'm guessing you are on Karmic)

---

### Post by logiconcepts819 on 2010-02-27
Now that I have replaced the most recent version of compat-wireless with the backport modules, my wireless connection works.  Thanks for your help.

Another P.S.: I tried using the wireless in 802.11n mode (with ieee80211n=1 set in hostapd.conf), but the wireless connection runs slowly and frequently disconnects, and eventually the wireless connection is permanently lost.  At this point, rebooting the server machine is the only choice to get the connection up and running again.  So, I decided to put the wireless in 802.11g mode (by commenting out the ieee80211n and ht_capab lines in hostapd.conf), and the connection runs very quickly and does not frequently disconnect.  I suppose this particular problem is related to [this bug]("https://dev.openwrt.org/ticket/6667").

---

