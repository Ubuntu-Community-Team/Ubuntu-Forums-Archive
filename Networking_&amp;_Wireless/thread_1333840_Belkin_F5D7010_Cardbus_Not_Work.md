---
title: "Belkin F5D7010 Cardbus Not Work"
date: 2009-11-21
forum: Networking &amp; Wireless
---

### Post by Scorpion2k5 on 2009-11-21
I have been useing linux now for about 10 years, I not an expert at it, but I know my around, this is the first time that I have had an issue with a network drive ever in my time using linux. I have a Belkin 802.11g F5D7010 Rev.1xxx and I have been trying all week everything that I know to get this card to work with Ubuntu 9.10, but nothing works. I had this card working just fine under 6.06, and 7.10, but nothing with 9.10. I don't want to have to go to another Linux Distro to get it to work. I know Fedora 12 works with it, I have it installed on my other laptop and use the same card on that laptop as well. 

I have tried to use NDISWRAPPER using the Window NT4, Windows 2000 and Windows XP drivers and nothing has worked. I have tried even to use the Broadcom 43xx driver directly and that hasn't been successful either... If you know anything that might work please let me know as soon as possible... Thanks.:D

---

### Post by Scorpion2k5 on 2009-11-21
I have run the lshw -C network and it came back with the card being a:
Broadcom BCM4306 802.11b/g Wireless LAN Controller (rev 03)

I have also don a lspci and that came back with the same result, not that I expected it to come back as anything else.

It says that Wireless is disabled, and the card is working properly, but there is no way to turn it back on... Am I missing something here??? Or am I just have and Senior moment... LOL

---

### Post by Scorpion2k5 on 2009-11-21
after a couple of hours of looking around on here I was able to find a link via the wiki links and i get to work... HERE IS THE LINK FOR ALL YOU FUTURE PEOPLE OUT THERE WITH BELKIN WIRELESS ISSUES.


[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by Scorpion2k5 on 2009-12-08
I have also found several other drivers on that site that work on 9.10, without problems. I hope that you all are finding your drivers as well.:popcorn:

---

