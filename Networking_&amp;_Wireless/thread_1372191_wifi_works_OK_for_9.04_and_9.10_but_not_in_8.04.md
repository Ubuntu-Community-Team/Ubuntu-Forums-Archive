---
title: "wifi works OK for 9.04 and 9.10 but not in 8.04?"
date: 2010-01-04
forum: Networking &amp; Wireless
---

### Post by ChipWolf on 2010-01-04
i am always using the latest version of ubuntu,but my main board of my acer5520g broke down under 9.10 last month,the acer company changed my main board and i installed 8.04-i386 LST for safety.
but i find the wireless card does not work, i search the google for help,it seems i should install madwifi,but i found no valid download,after a lot of attempts i surrender.
SO i put up this question
i need a driver for my wireless card (notebook type acer5520g ,wireless card AR 5B91(detected under windows (though i am a big fan of linux and a supporter,i am using two systems and waiting for the 10.04 LST to save me from virus braced windows) 
i even can not detect the wireless card under ubuntu 8.04 but it works ok in 9.04 and 9.10 after the installation.
Thanks.

---

### Post by ChipWolf on 2010-01-06
thanks to google and the original author it took me almost 6 hours to find a compromise solution :
use the compat-wireless-ath9k_20080916-debgen1_i386
download it,install it, then go to System>Administrator>Hardware Drivers enable it and reboot,you will see the wireless card is working.
because you can't use this driver to do aircrack ,it is called a compromise solution.
Can anybody help me to find a driver for this card to do aircrack test.
lspci -nn output by my system:
05:00.0 Network controller [0280]: Atheros Communications Inc. Unknown device [168c:002a] (rev 01)

my kernel 2.6.24-26

---

