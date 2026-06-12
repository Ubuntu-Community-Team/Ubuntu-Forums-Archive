---
title: "Wireless &amp; WPA"
date: 2005-01-18
forum: Networking &amp; Wireless
---

### Post by nocturn on 2005-01-18
Is there a way to enable WPA on Ubuntu Linux?

I'm running Warty with a prism54 supported card, WEP is working fine, but I'm a purist ;-)

---

### Post by mmuller on 2005-01-18
wpa would be cool. hopefully hoary might add support for it ? I too have a prism54 card and would like to secure my wireless at home again... since dropping winXP i have had to go with an open network...   8-[ 

Still, tis better to be open than lining BG's pockets...  :D

---

### Post by WTF_Shelley on 2005-01-25
[QUOTE=mmuller]wpa would be cool. hopefully hoary might add support for it ? I too have a prism54 card and would like to secure my wireless at home again... since dropping winXP i have had to go with an open network...   8-[ 

Still, tis better to be open than lining BG's pockets...  :D[/QUOTE]

You can still use wep128, I know its crackable but what isn't.

---

### Post by albersag on 2005-01-25
[QUOTE=WTF_Shelley]You can still use wep128, I know its crackable but what isn't.[/QUOTE]
 there are some utilities to audit your own network

Search aircrack for example. At full charge (tx 50 Kb/s) for example, in hours the wep keys could be obtained.

I do not use wep, as i have hacked my network multiple times ;)

Wpa is better but in linux it seems to be complicated. I have not try it .

---

### Post by gt500 on 2005-01-25
[QUOTE=nocturn]Is there a way to enable WPA on Ubuntu Linux?

I'm running Warty with a prism54 supported card, WEP is working fine, but I'm a purist ;-)[/QUOTE]
 try [www.linuxant.com/driverloader](www.linuxant.com/driverloader) and look for wpa ;)

greetz

---

### Post by eu/NEKE on 2005-02-13
Try wpa_supplicant... you can get it like this: sudo apt-get install wpasupplicant

note: it's in the universe repository, but it might not be in warty, I'm using hoary at the moment ;)

there's a nice howto on it at [http://www.ubuntulinux.org/wiki/WPAHowto](http://www.ubuntulinux.org/wiki/WPAHowto).

---

### Post by thezerogroup on 2005-12-16
WPA, is just as easy to crack as WEP

---

