---
title: "Compaq Presario CQ60 laptop wireless linksys internet not working"
date: 2012-01-31
forum: Networking &amp; Wireless
---

### Post by DrStupid962 on 2012-01-31
I have recently got a linksys wireless router and for the first couple of days it had work perfectly fine. Starting today it had stopped working and despite lurking around on the forums i had no luck as of now.
I have tried this code: ```
echo "options iwlagn 11n_disable=0" | sudo tee /etc/modprobe.d/iwlagn.conf
sudo modprobe -rf iwlagn
sudo modprobe -v iwlagn
sudo service network-manager restart
```and had no luck.
I would kindly appreciate some help since i am a noob at ubuntu and linux overall.

**_Additional info:_**
Computer: Compaq Presario CQ60 laptop
Linksys model: WRT120N
Ubuntu Version: 11.10
Any more info could be asked later.

Thanks in advanced.

---

### Post by DrStupid962 on 2012-01-31
Something i should mention, i cannot do anything related to the internet.
apt-get will not work so i have no idea how to download anything...
I am writing this from a family members computer in which is connected to the same internet connection and works.

---

### Post by DrStupid962 on 2012-01-31
instead of using "echo "options iwlagn 11n_disable=0" | sudo tee /etc/modprobe.d/iwlagn.conf" i used "echo "options iwlagn 11n_disable=1" | sudo tee /etc/modprobe.d/iwlagn.conf" and that still didn't work...

Ignore by above post, i can still connect with wired, but the whole wireless thing still poses as a problem.

I'm also not going to always have wired on me, i just got lucky

---

