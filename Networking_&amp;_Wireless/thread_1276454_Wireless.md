---
title: "Wireless :/"
date: 2009-09-27
forum: Networking &amp; Wireless
---

### Post by d00gy on 2009-09-27
well im a noob to ubuntu, but i cant get wireless working. I have onboard LAN 
(Realtek PCIE x1 LAN 8103EL / 8102EL)
but ubuntu wont recognize it. I dont know if i need to find drivers which ive looked and cant find anything. IU also have a Buffalo Airstation Wireless G usb from my old pc seeming that didnt have built in lan so i have 2 choices but neither of them work in ubuntu. Anyone that can help me? Im using 8.04. I searched my motherboard compatibility with ubuntu and someone said that onboard lan fine straight after installation.. On 9.04. can anyone tell me how to upgrade to 9.04 from 8.04 without internet connection

---

### Post by d00gy on 2009-09-27
Anyone?

my beffalo wireless is WLI-U2-KG1255
could i use WLI-U2-KG54L drivers or wont it work at all?

---

### Post by spd106 on 2009-09-27
This device should be supported by the rndis_wlan driver.

See [http://linuxwireless.org/en/users/Drivers/rndis_wlan](http://linuxwireless.org/en/users/Drivers/rndis_wlan)

If it's not working then you may need to fall back to using Ndiswrapper.
[http://ubuntuforums.org/showthread.php?t=370589](http://ubuntuforums.org/showthread.php?t=370589)

---

### Post by d00gy on 2009-09-27
Well i decided to use 9.04 seeming most people say it picks all your hardware up straight away but ive tried using wubi and from the boot menu. On the wubi screen the installation goes fairly quick  and i cant seem to boot into ubuntu as when i click it on the boot screen it just comes up witha  blinking cursor and black background. Ive tried booting it from the boot menu but i get stalled on a screen saying starting bluetooth devices, i have no bluetooth devices :S

---

