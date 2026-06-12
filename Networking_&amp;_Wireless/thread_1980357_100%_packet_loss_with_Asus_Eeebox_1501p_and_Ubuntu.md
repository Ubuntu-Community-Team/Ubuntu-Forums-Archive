---
title: "100% packet loss with Asus Eeebox 1501p and Ubuntu 10.04/12.04"
date: 2012-05-15
forum: Networking &amp; Wireless
---

### Post by stee on 2012-05-15
Hi,

My media center PC, an Asus Eeebox 1501p running stock Ubuntu 10.04 and XBMC has been stable and working great for about a year now. Last monday, that changed. Out of nowhere (after computer had been sleeping) I started getting 100% packet loss on my wifi, while the signal itself is strong (>95%). Other computers/phones work well, also in the same position. All units have static IPs, and nothing seems to be wrong, but I tried reassigning the eeebox to automatic IP and it didn't help.

The day before the problem, I did an apt-get dist-upgrade on this box, as well as an update from Mint 11 to Mint 12 on a laptop connected to the same network. The latter works great, but could it somehow have affected my other computer?

I thought the problem could have something to do with the kernel and the ath9k card - googling seems to bring up those, so I first tried to install the previous kernel, then the newest 3.x kernel and finally updated the whole system to Ubuntu 12.04. Nothing helped. 

Luckily, I have backup. I restored my /boot and / from partition images taken in May last year, when everything worked perfectly. I kept /home. To my surprise, the problem persisted. 

I am a bit lost. I could restore /home from an old partition image as well, but could I really expect that to help? Since I restored an old system, and it doesn't work, I guess the problem is likely to be somewhere else...

---

### Post by stee on 2012-05-16
Nevermind.  It was some sort of IP conflict, I believe. I disabled the previous IP address and turned on DHCP. Then I set up my android phone as an AP and connected my computer to it. Once I could connect to that, I knew there wasn't any hardware or driver problems, so I tried once more with my normal wifi network, but now with DHCP and the old IP "banned". Suddenly it worked again.

---

