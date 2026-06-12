---
title: "D-Link DWL-G520"
date: 2006-06-12
forum: Networking &amp; Wireless
---

### Post by Topfs on 2006-06-12
I am having some difficulties getting my wireless network card running in Ubuntu 6.06 LTS with the supplied MadWifi drivers. Is there any howto that I can use? I have googled and searched this forum but cannot find anything that relate to this problem?

I cannot connect to any wireless network, Open, WEP or WPA but I can scan for them as Network manager picks them up beutifully. Used this guide but skipped the part with installing intel wireless drivers: [http://www.ubuntuforums.org/showthread.php?p=1128894#post1128894](http://www.ubuntuforums.org/showthread.php?p=1128894#post1128894)

I have used this card succesfully with both OpenSuSE 10.0 standard and madwifi drivers and OpenSuSE 10.1 madwifi, with full WPA support. So it should work I think.

I have tried both the supplied driver in i386 and i686 with no luck. I think I updated to some cvs version also but on that install I tried everything so I might have screwed it up badly that time so I have now a fresh install and I have only followed that guide.

Please please help me I have fallen for Ubuntu and I think it beats OpenSuSE on almost any point with the exeption of Wireless so if anyone can help me get pass this issue please please do :)

/Tobias

---

### Post by Topfs on 2006-06-13
Got it working with WPA-PSK!

Followed the mentioned guide: [http://www.ubuntuforums.org/showthread.php?t=125150](http://www.ubuntuforums.org/showthread.php?t=125150)

Skipped the driver update (For obvious reasons) but did the ieee80211 update and finished the installation of with

```
svn checkout http://svn.madwifi.org/trunk madwifi
cd madwifi
make
sudo make install

```

Posting on WPA encryption as we speak!
Thx a million Jeff250 you truly saved my day!

---

