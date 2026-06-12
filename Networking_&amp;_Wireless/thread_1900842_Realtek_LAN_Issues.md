---
title: "Realtek LAN Issues"
date: 2011-12-27
forum: Networking &amp; Wireless
---

### Post by tommiy on 2011-12-27
I upgraded my BIOS on my ASUS P5G41C-M LX to the latest version (0702) from 0402. After doing this my LAN card no longer appears to wish to function. This is the onboard RLT8112L or 8168D by another name by the looks. (Ubuntu 11.10) Basically, the card still seems to be able to work with static addressing...I can ping other PCs on the same segment however DHCP no longer functions. More specifically if I look at my router logs while the card is trying to get an address I do not even see a single request.

If that is not strange enough I down loaded the DOS test program from realtek RSET8168 and it tests the card and states its all good except for the EEPROM test where it states that the EFUSE data is wrong. Searching on that I found the Realtek program to reprogram the the chip at 

translate.google.com.au/translate?hl=en&sl=zh-CN&u=http://www.biostar.cn/app/en-us/support/faq.php%3FS_ID%3D413&ei=w4r5Tp-JJcaaiAf6373CAQ&sa=X&oi=translate&ct=result&resnum=21&ved=0CNQBEO4BMBQ&prev=/search%3Fq%3DPG8168%26num%3D100%26hl%3Den%26client%3Dfirefox-a%26hs%3DI4T%26rls%3Dorg.mozilla:en-US:unofficial%26prmd%3Dimvns

Doing a 
pg8168 /r
and
pg8168 /r /efuse

gives me 2 different values for the MAC address. The first seems to be correct and the second incorrect. I don;t know if this is correct and I'm chasing a wrong tree or something else. If anyone else has a P5G41c-M LX I'd appreciate if you could run the commands and tell me if they match. They are only read commands so no harm.

Shear desparation I tried windows 7...it too fails with a code of 10 which means it can not load the driver successfully. No more information...

If anyone has any other ides please let me know...I'm at my wits end with trying to get this to run. Think I'll by a stand alone NIC card and simply use that because I can;t get this thing to work with DHCP at all any more. Thanks

---

### Post by gaby81 on 2012-08-02
You shouldn't use the "efuse" mac address. efuse setting are used only in case the eeprom fails, so the data loads from efuse.
In other, less geeks words - use pg8168 /r for getting the correct mac address

---

