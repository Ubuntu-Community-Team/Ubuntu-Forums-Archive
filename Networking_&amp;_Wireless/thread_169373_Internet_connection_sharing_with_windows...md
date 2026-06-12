---
title: "Internet connection sharing with windows.."
date: 2006-05-02
forum: Networking &amp; Wireless
---

### Post by astriskmanish on 2006-05-02
hi there,
I m using UBUNTU for 64 bit pc with a PC having WINDOWS is connected to me(no hub no switch just PC to PC connection) and i dont know how to share internet connection which is on my PC with a dialup connection. So can any one tell me how to give or share connection with that PC on my network. Ya plz tell me the commands also b'coz i m bit new in this linux.

---

### Post by Iowan on 2006-05-03
Have you verified that the two boxes communicate (ping)?
Is the Windows box set up to share internet?

---

### Post by astriskmanish on 2006-05-03
[QUOTE=Iowan]Have you verified that the two boxes communicate (ping)?
Is the Windows box set up to share internet?[/QUOTE]
ya the two box r connection and also file sharing is there between the two through **samba**, but when i connect my pc to internet through dialup connection then the other box didnt get that connection.......

---

### Post by Slim Odds on 2006-05-03
[QUOTE=astriskmanish]ya the two box r connection and also file sharing is there between the two through **samba**, but when i connect my pc to internet through dialup connection then the other box didnt get that connection.......[/QUOTE]

The machine that is going to use the shared connection has to have a route to the outside world.

Output from ifconfig and route -n would help us help you.

---

