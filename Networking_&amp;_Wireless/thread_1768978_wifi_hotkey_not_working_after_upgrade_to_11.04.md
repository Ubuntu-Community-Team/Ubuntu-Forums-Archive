---
title: "wifi hotkey not working after upgrade to 11.04"
date: 2011-05-27
forum: Networking &amp; Wireless
---

### Post by dixie1755 on 2011-05-27
Hi, after upgrading to 11.04, I can't use the fn-f2 combination anymore to activate the wifi card. I'm using a Dell latitude laptop. Wifi is functioning normally when it's on and I can even turn it off with the hotkeys. When I try to turn it back on, the light goes on for a second and than dims again. I than have to reboot into Windows to get it back on, which is kind of annoying.
Does anybody know how to fix this?
Thanks!

---

### Post by josephmills on 2011-05-27
hi there could you please open your terminal and type in ```
rfkill list all
``` and paste here thanks

---

### Post by dixie1755 on 2011-05-28
Hi, below the first output is with the wifi on, the second after I used the hotkeys to turn wifi off.
david@ubuntu:~$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
david@ubuntu:~$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

---

