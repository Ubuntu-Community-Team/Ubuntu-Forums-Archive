---
title: "Wireless Issues"
date: 2011-06-13
forum: Networking &amp; Wireless
---

### Post by CyberShadow_D on 2011-06-13
I wiped out my old version of Ubunto and installed 11.4 but now Im getting no connection whatsoever... Im not that familiar with this OS as I only use it on my touch panel laptop so Im lost as to what to do. Tried DL'ing the drivers but that didn't work. 


Here are some screenshots of iwconfig, ifconfig and lspci if it helps.

THANKS!

[[COLOR=#22229c]http://imageshack.us/photo/my-images...eenshotka.png/[/COLOR]]("http://imageshack.us/photo/my-images/837/screenshotka.png/")
[[COLOR=#22229c]http://imageshack.us/photo/my-images...enshot1oy.png/[/COLOR]]("http://imageshack.us/photo/my-images/691/screenshot1oy.png/") __________________

---

### Post by CyberShadow_D on 2011-06-14
Anybody???

---

### Post by tuxonapogostick on 2011-06-14
After doing the same mistake as you, I concluded it best not to upgrade to new ubuntu for a while if you are happy with the current version. Anyways. Can you do lspci one more time with the verbose option and post the output:
```
lspci -v
```Also can you post the output of:
```
lsmod
```P.S.: can you post the output of these commands in text form rather than image. That way some important keywords can be search by search engines. So, on terminal select the text, right click, and do copy. Then paste it to the thread.

---

### Post by tuxonapogostick on 2011-06-14
It seems like you have **BCM4306** wireless card. Have you searched for the threads including this keyword? I found the following one for example:
[http://ubuntuforums.org/showthread.php?t=1604868&highlight=bcm4306](http://ubuntuforums.org/showthread.php?t=1604868&highlight=bcm4306)

---

