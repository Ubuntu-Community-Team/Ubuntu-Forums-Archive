---
title: "flash is jumpy"
date: 2009-09-12
forum: Multimedia Software
---

### Post by cocheese on 2009-09-12
[LEFT]installed ubuntu just 2 days ago for the first time and im trying to iron out the issues.
Flash is working - fully installed but when i try and play anything full screen it gets jumpy. Ive read it might be a graphical issue but i dont think so because i have a geforce 8800GT and short of compatability issues it cant be the cause i think. Also the jumping effects the gameplay on flash games. So i think its a problem with flash itself.

I tried using this code
```
sudo apt-get purge adobe-flashplugin flashplugin-nonfree gnash gnash-common libflashsupport mozilla-plugin-gnash nspluginwrapper swfdec-mozilla && sudo apt-get install flashplugin-nonfree
```

not sure what it does but it didnt work lol.

Help please  :S
[/LEFT]

---

### Post by jfernyhough on 2009-09-12
Are you running 32-bit or 64-bit? (If running 64-bit use the 64-bit plugin from the Adobe labs.)

Which drivers are you using for your Nvidia card? (Try the 190 series.)

Do you have hardware acceleration enabled in Flash?

---

### Post by cocheese on 2009-09-12
with the (so far) singular exception of a particular game that ive found (not sure if i can link). this error seems to have disappeared when i reinstalled gnome. would still really like to solve it. its a really good game :S
i think im on 32 bit... but i dont know. dont know about the driver either and yeah i already disabled the hardware accelerator.

---

### Post by carl4926 on 2009-09-12
In a terminal do
```
uname -a
```
post result

---

### Post by cocheese on 2009-09-13
Linux dan-desktop 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux

---

