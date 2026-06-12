---
title: "no network at all"
date: 2010-01-14
forum: Networking &amp; Wireless
---

### Post by papaupa on 2010-01-14
Hi guys i just installed ubuntu in 1 of my boxes is an old compaq presario v2000. Is running dual boot with XP, the problem is i dont have internet connection(wireless and wired) with Ubuntu but i do with XP. I read like hundreds of posts from diferent forums and i wrote all crazy commands in terminal but aint working. I tried directly trough the modem (motorolla 2210)and with the router(netgear wgr614) via wired and wireless and aint working  either. For some reason  ubuntu doesnt request an ip adress from the router or the router dont asign an ip adress to my linux box. Plz guys take it ez with me im really new in linux. Thanks in advance.

---

### Post by gabo.cr on 2010-01-14
You only have one post in this forum, so I don't know what kind of commands you tried.
What info do you get when you connect the computer to the router with a network cable using this command?

```
ifconfig
```

---

### Post by Matt_Johnson on 2010-01-14
ndiswrapper try that.

---

### Post by papaupa on 2010-01-14
Hey Gabo thanks for the reply,like i said im really new in this linux stuff. When i type ifconfig this is why i get:

eth0  Link encap:Ethernet Hwaddr 00:16:36:79:82:CF
      UP BROADCAST MULTICAST MTU:1500 METRIC:1
      RX packets:0 errors:0 dropped:0 overruns:0 frame:0
      TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:1000
      RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
      Interrupt:209 Base address:0xe000
     
 lo   Link encap:Local Loopback
      inet addr:127.0.0.1 Mask:255.0.0.0
      inet6 addr: :1/128 Scope:Host
      UP LOOPBACK RUNNING  MTU:16436 METRIC:1
      RX packets:240 errors:0 dropped:0 overruns:0 frame:0
      TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:0
      RX bytes:17708 (17.2 KiB) TX bytes:17708 (17.2 KiB)

Any help is good bro, thank you

---

### Post by papaupa on 2010-01-14
> **Matt_Johnson said:**
> ndiswrapper try that.

hi, hey i download something like that and installed it but didnt worked. I dont know if i need to do something after run that or probably i downloaded the wrong one. Im kind of dumb in this linux stuff bro i need a walkthrough im kind of dumb in this. Thank you

---

### Post by d3v1150m471c on 2010-01-14
what kind of internet are you trying to setup?

---

### Post by papaupa on 2010-01-14
> **d3v1150m471c said:**
> what kind of internet are you trying to setup?

i have dsl . I want to setup both wired and wireless.

---

### Post by papaupa on 2010-01-14
Bump!!! cmon guys i need ya help,im flying by myself and i dont know how to fly!!!!! lol.

---

