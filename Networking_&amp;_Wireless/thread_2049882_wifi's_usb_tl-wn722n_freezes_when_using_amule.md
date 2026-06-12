---
title: "wifi's usb tl-wn722n freezes when using amule"
date: 2012-08-29
forum: Networking &amp; Wireless
---

### Post by tanzak on 2012-08-29
Hi,

i'm using usb wifi card tl-wn722n from tp-link with my ubuntu 12.04. It works fine, but when i use amule, and after a while (sometimes 1 hour and simetimes 15 minutes), it freezes and the computer gets disconnected from the internet. Sometimes the stick gets freezed with the led switched on, and sometimes the led is switched off. Then i have to unplug it and plug it again in to a different port so it gets connected again and the computer connects to the internet. Also, sometimes, the computer itself freezes and i only see a black screen with a violet line on the top, and there is nothing i can do except pressing the reset button. 

Anyone knows how to solve this problem?, or at list detect where the problem comes from....? I've been searching in the log files but i don't know which log should i read and what to search for...

thanks to all

---

### Post by praseodym on 2012-08-29
Hi,

try to deactivate the hardware encryption of the driver:

```
echo "options ath9k_htc nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k_htc.conf
sudo modprobe -rfv ath9k_htc
sudo modprobe -v ath9k_htc
```
Change the encryption mode to pure WPA2 only, if possible. See the router manual for this.

---

