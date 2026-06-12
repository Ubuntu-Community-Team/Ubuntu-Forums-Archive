---
title: "Dell WLAN 1520/Ubuntu 10.x(Latest)/Dell Vostro 3300"
date: 2010-06-17
forum: Networking &amp; Wireless
---

### Post by rahuljuneja on 2010-06-17
I was trying to install ubuntu latest version on my laptop Dell Vostro 3300 and thought of trying first with the bootable pen drive. 

Once i booted the system with Ubuntu, as far as i know everything worked pretty nicely and was impressed with the stuff, but the only issue i had was wireless was not working. I have home wireless network and use WPA/WPA2 passphrase security on it. I also tried installing the drivers by just fiddling around but nothing seems to help. Is there any link or guide which tells me exactly what do in need to do to get the driver for the above mentioned version and how to install it.

Any help on this is highly appreciated.

PS: My previous laptop Dell vostro 1310, I was able to install th e wireless broadcoom drivers and run the wireless 
Thanks,
Rahul

---

### Post by Shazzam6999 on 2010-06-17
What wireless card are you using?
```
lspci -nn | grep -i net
```

Err and did you just upgrade to a new version? Because 10.04 seems to have some wireless problems.

---

### Post by rahuljuneja on 2010-06-17
I am not completely sure as i don't have the access to my system right now but i guess it is Broadcom 463CA85929AAAF3380E.. I will post the exact number in few hours. and to answer your other question, yes i am using 10.04 which i recently downloaded. 

Is there any other version, which which does support this driver out of the box.

Thanks,
Rahul

---

### Post by Shazzam6999 on 2010-06-17
Assuming that it's the same broadcom card I have (4312)I think 9.10 supports it out of the box. And I know that the distribution Crunchbang supports it out of the box; but I'm assuming that's because it's based off 9.10. If you want to check without installing anything try out the livecd and see if it works.

---

