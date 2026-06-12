---
title: "yet another intel pro/wireless issue"
date: 2009-08-15
forum: Networking &amp; Wireless
---

### Post by wmmubu on 2009-08-15
yet another intel pro/wireless issue

(3945ABG) works with live cd ubuntu 9.04 but not with live cd kubuntu 9.04

i post this only to add to the pool of symptoms.

i've noticed at least a couple of subscribers who say installing xfce cures their iwl3945 ills - this seems like a bit of overkill.  

i guess i could try wicd, but it seems that if using raw iwconfig doesn't work, something below ntwk mgr and/or wicd is broken.

the facts follow:

the live cd Kubuntu is approx 2wk old on-disk.com 'always up to date' version dated 27 july 09, kernel version 2.6.28-11
the live cd (gnome)ubuntu is dated 17 apr 09, kernel version 2.6.29-11

running on toshiba satellite A105.

the steps to failure:
  iwlist scanning shows several cells.  running it again shows only one.
  use NetworkMgr to set up essid, key (in hex), automatically connect, click OK
  small box pops up labelled 'enter network connection, - enter key, click OK
  popup from sys tray immediately says 'connection on wlan interface failed'

interesting things:
  inside ntwk mgr, the 'scan' button shows multiple networks avail
  one of the listed cells is my wireless router - the enet address is correct. - tells me the drivers and wifi h/w work

iwlist shows (among others) my router, the enet addr is correct.

iwconfig shows the intf status as UP, but no addr - tells me dhcp can't do it's thing.  yes, the key is cut and paste'd from the same place as when it works on other distribution.
 
iwconfig shows 'access point: not-associated'.
  iwconfig also shows essid is not what i put in, but it is a valid UN-encrypted cell detected by the 'scan' button in NM.  also shows no encryption - tells me the intf fell back to the first unencrypted link.  the essid is that of a local pay hot spot, but the intf does not connect.  

lsmod shows iwl3945 version 1.2.26ks as being loaded.
  network mgr shows the intf device as being wlan0, yet lshw -C network seems to think it should be wmaster0 (logical name: wmaster0) - not sure what this tells me.  note also lshw does not list the driverversion: but lists 'driver=iwl3945' in the configuration: line. works this way on the (gnome)ubuntu version as well.  diff version of lshw?


next: 
config wlan0 using iwconfig wlan0 key and essid, then
config route to the router and default route - no help

after manual config using iwconfig, ifconfig wlan0 shows the expected stuff, except it still shows 'access point: not-associated'.  also, iwlist scanning now shows only my wifi router.  not sure if this is to be expected or not.

on (gnome)ubuntu, iwlist scanning (before being setup for my router) shows only the pay site, yet the popup/hover of the ntwk connectivity bars shows multiple cells.  (i guess i would have thought the gui app uses iwlist.  hmmm...)

dhclient (both with and without -r) give a couple of 'unknown hardware address type 801'.  dhclient wlan0 also gives several DHCPDISCOVER lines, but ends with no offers rec'd.

reconfig wlan0 to be fixed addr via ifconfig wlan0 10.10.10.100.  ping 10.10.10.1 fails (but no longer says 'no route', now pings a few times then says 'no route'

lsmod shows iwl3945 as being loaded.
gnome ubuntu lsmod and Kubuntu lsmod is the same except gnome version has a module called binfmt_misc that Kubuntu does not.  unrelated, i think.

iptables is disabled.

ideas?

---

### Post by x22 on 2009-08-17
welcome to the forum

have you installed the firmware?

[http://www.intellinuxwireless.org/?p=iwlwifi&n=downloads](http://www.intellinuxwireless.org/?p=iwlwifi&n=downloads)

---

