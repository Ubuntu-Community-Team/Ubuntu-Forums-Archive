---
title: "Wireless not switching on"
date: 2013-07-19
forum: Networking &amp; Wireless
---

### Post by printer305 on 2013-07-19
I have a lenovo Ideapad Z570. I dropped it (wince) once and luckily enough, nothing happened except that the hardware switch for my wireless internet stopped working and some denting. Fn+F5 still switched on wireless though. So that was pretty much fine. This was with Win 7. Later, I shifted to Win 8 and Fn+F5 would turn airplane mode on and off so I didn't have wifi. Shifted to Ubuntu a few months back and wifi doesn't work whether I use fn+f5 or the switch. The switch turns on only bluetooth, not wifi. I tried what was given here: 
[http://ubuntuforums.org/showthread.php?t=1737824&page=2&highlight=wireless](http://ubuntuforums.org/showthread.php?t=1737824&page=2&highlight=wireless)
```

 rfkill list all
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```

So anyways, as an alternative (without opening up my laptop) I was looking at the ASUS USB N10 Wireless adaptor. However, here
[http://ubuntuforums.org/showthread.php?t=2066104](http://ubuntuforums.org/showthread.php?t=2066104)
It says that my internal wireless should be on to use it, and thats something I can't do. Does anyone know if this is a viable option for me? If not, what other options do I have?

---

