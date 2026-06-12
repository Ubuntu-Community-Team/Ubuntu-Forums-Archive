---
title: "Very slow wireless internet"
date: 2013-02-14
forum: Networking &amp; Wireless
---

### Post by danielgabbe on 2013-02-14
Hello everybody!
I have got a descktop running ubuntu 12.04 (kernel is 3.2.0-37-generic-pae) 
ADSL wifi router model D-Link DSL 2640U and usb wifi dongle *TP*-[I]LINK TL-WN422G
When I check the speed using Speedtest.org it shows [/I][I]0.4 - 0.6 Mbps

[/I]Althogh Ipad2 wich i use via the same router shows speed at about 3.5 - 4.2 Mbps. 

I have read that my dongle should work great without any additional drivers on Ubuntu 10.04 and older. But that appeared not to be true( 
How this could be solved?
I'm fresh in linux, so the best I can do is to cut'n'paste commands to Terminal.

---

### Post by praseodym on 2013-02-14
Check the driver:
```

lsmod | grep ath9k_htc
```
If it is yours, deactivate the hardware encryption:

```
echo "options ath9k_htc nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k_htc
sudo modprobe -v ath9k_htc
```

---

