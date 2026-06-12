---
title: "Manual connection works, /etc/network/interfaces doesn't."
date: 2009-09-07
forum: Networking &amp; Wireless
---

### Post by verv87 on 2009-09-07
```
sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "essidname"
sudo dhclient wlan0
```
^ This works.

/etc/network/interfaces
```
# Loopback
auto lo
iface lo inet loopback

# Interfaces
auto wlan0
iface wlan0 inet dhcp
    wireless-essid essidname
```
Then:```
sudo /etc/init.d/networking restart
```
^ This doesn't work. iwconfig doesn't associate.

How do I make /etc/network/interfaces work like the manual connection?

---

### Post by ninja123 on 2009-09-25
hi there!

I have the same problem so was just wondering if you could help me.

Have you resolved yours? If yes, what did you do??

---

