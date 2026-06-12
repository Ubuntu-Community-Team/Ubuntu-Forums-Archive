---
title: "Strange Wireless Issue"
date: 2012-12-21
forum: Networking &amp; Wireless
---

### Post by Beren6 on 2012-12-21
Hello All:

I'm wondering if anyone might be able to provide some insight into a strange wireless issue. 

I recently installed Ubuntu 12.04. Initially, the wifi barely worked (wouldn't connect, or was verrrry slow if it did). After figuring out what driver I was using (ath9k), I checked the forums and used the solution involving turning off hardware encryption, this:

sudo ifconfig wlan0 down
sudo rmmod -f ath9k
sudo modprobe ath9k nohwcrypt=1
sudo ifconfig wlan0 up

At this point the connection enabled and worked flawlessly. As the forums recommended, I created a file containing the line 
options ath9k nohwcrypt=1 
in the file 
/etc/modprobe.d/ath9k.conf
The next time I booted the Wifi started up again and worked fine.

Now here's the strange part: the next time I booted into Ubuntu, the wifi would not connect at all. The card was clearly detecting the networks and attempting to connect, but just kept failing and retrying over and over. I tried the above solution again to no avail.

Just to make sure it wasn't something physically wrong with the card, I booted into my Windows partition (XP pro SP3), where the wifi worked fine. I then rebooted into Ubuntu and, to my surprise, the wifi connected right away.

Just to check, I've tried several different combinations, and, sure enough, if I boot from a shutdown state directly into Ubuntu, no love from the Wifi; however, if I boot into Windows first and then reboot into Ubuntu, the wifi connects right away. 

Would anyone have any thoughts about why this might be the case--and, if so, how I might get Ubuntu working properly (I've become enough of a Linux user that I rarely boot into Windows anymore, and then usually only to play Windows-specific games).

Thanks!

---

### Post by Pjotr123 on 2012-12-21
Maybe this helps:
[https://sites.google.com/site/easylinuxtipsproject/internet](https://sites.google.com/site/easylinuxtipsproject/internet)

---

