---
title: "command help"
date: 2011-08-21
forum: Networking &amp; Wireless
---

### Post by raja.genupula on 2011-08-21
i have a usb modem . i need a help on the bash command which is used to connect my usb modem from terminal . i know ifconfig , its displaying all my connections and usb modem also . by using that i can stop my net but i cant make it up . can nay one help on this . 

thanks in advance

---

### Post by raja.genupula on 2011-08-22
c'mon , could any one give me support . 
i know how to use ifconfig generally for eth0 connection but i dont know for my modem . please ...

---

### Post by dave01945 on 2011-08-22
what sort of modem is it is it a mobile broadband dongle

---

### Post by raja.genupula on 2011-08-22
yes 
may be you need this 


```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by dave01945 on 2011-08-22
the easiest way i have found for setting up mobile broadband on linux is with a script called sakis3g it has everything you need in it and will guide you through the whole setup 

here is there website
[http://www.sakis3g.org/](http://www.sakis3g.org/)

you can get any info you need there but all you need to do is make the script executeable using 

```
chmod +x sakis3g
```

and then run it with this command

```
./sakis3g --interactive
```

if your network is not listed you just need to enter the access point manually

i would upload you a copy but the forum wont let me you can download it from their website it's the best way i have found to use these devices

---

### Post by raja.genupula on 2011-08-23
thank you very much , i will look at that when i get back to my room .

---

