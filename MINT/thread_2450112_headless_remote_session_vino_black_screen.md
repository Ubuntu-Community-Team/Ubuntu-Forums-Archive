---
title: "headless remote session vino black screen"
date: 2020-09-07
forum: MINT
---

### Post by sailingboyLLB on 2020-09-07
hi all,


i have a desktop with amd 3200G cpu that i run headless. i'm trying to connect via vnc, but when i do i get only a black screen. this is with a fresh install of mint 20 cinnamon and all updates installed. this setup previously worked with ubuntu 19.10.


i have installed vino following these instructions:
[https://forums.linuxmint.com/viewtopic.php?t=272356](https://forums.linuxmint.com/viewtopic.php?t=272356)


i have installed a dummy display following these instructions:
[https://askubuntu.com/questions/1033436/how-to-use-ubuntu-18-04-on-vnc-without-display-attached](https://askubuntu.com/questions/1033436/how-to-use-ubuntu-18-04-on-vnc-without-display-attached)


when connecting via vnc, it detects the server, does the password authentication, and then brings me to a black screen.


any help is much appreciated. thanks.

---

### Post by QIII on 2020-09-07
Moved to MINT as a more appropriate forum.

Although Mint is derived from Ubuntu, it is an entirely independent distribution and is not one of the official flavors of Ubuntu.

---

### Post by sailingboyLLB on 2020-09-11
if anyone is looking for the solution that worked for me, i missed an option in dconf to disable approval prompt when connecting remotely. after changing this everything worked as expected.

---

