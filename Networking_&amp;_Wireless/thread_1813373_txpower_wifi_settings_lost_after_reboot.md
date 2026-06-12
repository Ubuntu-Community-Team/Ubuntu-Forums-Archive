---
title: "txpower wifi settings lost after reboot"
date: 2011-07-27
forum: Networking &amp; Wireless
---

### Post by ebb5 on 2011-07-27
I turned down my txpower with the command:

sudo iwconfig wlan0 txpower 3

Which works to fine turn down my broadcast power from the default value of 15 dBm to 3 dBm.  But it is reset every time I restart Ubuntu 11.04 to the default value of 15 dBm. 

Can someone please help:  How do I save my modified  txpower settings so they don't reset after a restart?  It is really annoying having to re-enter the  command every time I reboot my computer!

---

### Post by thefasterblueone on 2011-07-27
Add this to your rc.local.

```
sudo gedit /etc/rc.local
```

Add it right below this line:
_# By default this script does nothing._

```
iwconfig wlan0 txpower 3
```

then:

```
chmod u+x /etc/rc.local
```

to make it run at boot.

---

### Post by ebb5 on 2011-07-27
Thank you!

---

