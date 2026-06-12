---
title: "Wireless Internet not working in Ubuntu 10.10"
date: 2010-10-10
forum: Networking &amp; Wireless
---

### Post by Inderrawal on 2010-10-10
Hi There,

I just now installed Ubuntu 10.10 on my Lenovo Thinkpad X41 it did connect to the wireless internet at the time of installation but failed to connect after the installation was complete and i restarted the computer. It keeps on asking me the Key but for some reason doesn't take it. I have Intel PRO/wireless 2915 ABG network card.

---

### Post by undecim on 2010-10-10
just FYI, I'm having this issue with my Intel WiFi Link 5100 card. It was working for one boot after installation, and I'm looking into it.

I installed the RC a few days ago, and have updated since. The disk I installed from can connect, but not my installed system, so I suspect this is a bug brought by an update.

---

### Post by dl_sledding on 2010-10-10
EDIT: I am retracting this, as I am on 10.04, not 10.10.

Ditto here on an old Toshiba 1400.  Worked on 9, but after the upgrade it simply loops through "Authentication required by wireless network", and I don't have WPA, just WEP.

---

### Post by dineshs on 2010-10-11
Please see if these links can help
[http://ubuntuforums.org/showpost.php?p=9680300&postcount=14](http://ubuntuforums.org/showpost.php?p=9680300&postcount=14)
[http://ubuntuforums.org/showpost.php?p=9767936&postcount=11](http://ubuntuforums.org/showpost.php?p=9767936&postcount=11)

---

### Post by conualfy on 2011-05-01
It's been a while since the upgrade to 11.4 and it's not so nice to know  that something basic as a wifi connection that should just work out of  the box it's not actually working.
Reconnecting the wifi connection makes the internet work again, but it's  just a matter of minutes or seconds before I have to do this operation  again.

I have changed the router encryption to none (I've lowered security by  using only the MAC filter) and there is no difference, it's showing that  I'm connected to the router, but the internet is not working at all.

I've just tried disabling the IPv6 and the bug is still here.

I tested the connection with this script:
[http://sourceforge.net/projects/wirelessscript/files/](http://sourceforge.net/projects/wirelessscript/files/)
The results for both the working wifi and the one not working (but showed by the network manager as connected) here:
[http://goo.gl/hyrZg](http://goo.gl/hyrZg) (reconnected, wifi working)
[http://goo.gl/sdgwL](http://goo.gl/sdgwL) (wifi not working)

I would allow some good willing specialist to debug this on my computer  or any other way he/she suggests. If there is anyone interested in  fixing this nasty bug, please send me an email on florin [at] drumliber  [dot] ro


PS: I'm using a laptop (Toshiba Satellite C650 with Atheros wifi card and wifi under Windows 7 work perfectly.

---

