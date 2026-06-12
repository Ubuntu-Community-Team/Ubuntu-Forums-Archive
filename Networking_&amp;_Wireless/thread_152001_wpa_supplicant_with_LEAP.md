---
title: "wpa_supplicant with LEAP"
date: 2006-03-29
forum: Networking &amp; Wireless
---

### Post by Xephonic on 2006-03-29
Hi, my college requires leap authentication. I decided to give wpa_supplicant a shot.
i also use linuxant driverloader btw. Anyways...
i configured my file but...whenever i try to connect to my configured network i get this message in STATUS: ASSOCIATING
 Association to driver request failed....any ideas?

---

### Post by jml on 2006-03-29
A couple ideas to start with.  Are you certain that the wireless card supports WPA_supplicant.  I spent over a week trying to get it to work on a card with thr RT2500 chioset before I discovered that WPA_supplicant did not support it.   Second idea, according to the wpa_supplicant web site:

[http://hostap.epitest.fi/wpa_supplicant/](http://hostap.epitest.fi/wpa_supplicant/)

leap is only supported with special driver support.  I don't know exactly what that refers to, but it sounds like you may have to jump through a few hoops to get leap working.

Joe

---

### Post by Xephonic on 2006-04-06
That all may very well be the case. I noticed the special driver support too, but i had no idea what it meant.

---

