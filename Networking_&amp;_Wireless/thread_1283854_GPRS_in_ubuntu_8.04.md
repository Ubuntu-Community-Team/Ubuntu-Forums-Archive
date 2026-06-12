---
title: "GPRS in ubuntu 8.04"
date: 2009-10-06
forum: Networking &amp; Wireless
---

### Post by roshgorg on 2009-10-06
Hi, I installed Ubutu 8.04 and  wished to access internet using my GPRS enabled mobile phone... I configured the wvdial.conf from the instructions i found over the internet, and i connected to the internet just once. The firefox loaded different webpages... after sometime, the net was somehow disconnected because of some incoming calls to my phone...Aftr I attended, and reconnected the internet by typing wvdial in the terminal, it was connected, but , firfox was not loading any websites..,but the update manager was working..I downloaded codecs for playing mp3 files...and update manager was also downloading files, but firefox wasnot working.. Why is this? please help.

---

### Post by GeorgeVita on 2009-10-06
Hi **roshgorg**,
this is a 'old bug' that starts firefox in offline mode. Turn 'work mode' from firefox 'File; menu (**ALT+F W**).

A permanent solution is to change an internal parameter:
> **pj_kare said:**
> Typing about:config into firefox address bar and changing toolkit.networkmanager.disable from false to true (just by double clicking that line) also fixes offline issue. :)

Regards,
George

---

