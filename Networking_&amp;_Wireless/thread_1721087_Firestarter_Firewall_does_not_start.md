---
title: "Firestarter Firewall does not start"
date: 2011-04-04
forum: Networking &amp; Wireless
---

### Post by voiceofsummer on 2011-04-04
Hello, everyone :)
Here's the thing:
I placed my hard drive with ubuntu 10.10 from one box to another (different hardware). Everything works just fine except Firewall via Firestarter software does not start - says connection eth0 is not ready. The thing is there's no eth0 connection anymore - it is now eth2. I tried to run wizard, it shows everything is okay, but error remains. Even tried to rename the connection - nothing.
Would appreciate any help, thanks.

---

### Post by dmizer on 2011-04-04
You are welcome to use Firestarter, but I strongly suggest that you do not. Active development for Firestarter stopped in 2005. You should use UFW instead. You can install a nice graphic interface for UFW called "GUFW" with the following command:
```
sudo apt-get install gufw
```
You can also install GUFW with Ubuntu software center or in Synaptic.

Once GUFW is installed, then you can find your firewall configuration in System > Administration > Firewall Configuration.

---

### Post by voiceofsummer on 2011-04-04
thanks a lot :) already installed it.

---

