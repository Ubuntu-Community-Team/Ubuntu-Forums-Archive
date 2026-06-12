---
title: "After installing virtual box in hardy heron, eth0 and ath0 interfaces were lost"
date: 2009-04-04
forum: Networking &amp; Wireless
---

### Post by DeepSeaNautilus on 2009-04-04
Hello, I recently installed virtual box in my ubuntu 8.10 netbook, because its free and I want to use to virtualize win xp in my machine. I downloaded the .deb file from virtual box homepage, it asked me if I wanted to compile the headers and I said yes. It seemed to install ok, but then I realized that my eth0 and my ath0 network interfaces were lost. I tried to use ifconfig eth0 up to configure my ethernet connection, but It is not working. When I try to use wlanconfig for creating ath0 interface, I get an ioctl error message. Can anyone help please?

---

### Post by EoRaptor013 on 2009-04-04
I don't know a lot about the subject, but I started having network problems when I upgraded to 8.10. I read in this forum about an open source product called WICD ( [http://wicd.sourceforge.net/download.php]("http://wicd.sourceforge.net/download.php") ). I installed that and my network problems were cured. 

Of course, the real question is what happened in the first place. That I can't help you with.

Randy

---

### Post by cariboo on 2009-04-04
Could you post the output of:

```
ifconfig
```

in your next post.

Jim

---

### Post by DeepSeaNautilus on 2009-04-04
I do not have my netbook right now, but the output of ifconfig is only the loopback interface lo.

---

### Post by superprash2003 on 2009-04-05
try restarting networking by typing **sudo /etc/init.d/networking restart** in the terminal

---

### Post by DeepSeaNautilus on 2009-04-06
> **superprash2003 said:**
> try restarting networking by typing **sudo /etc/init.d/networking restart** in the terminal

I did that, but it did not solve my problem.

---

### Post by DeepSeaNautilus on 2009-04-07
> **cariboo907 said:**
> Could you post the output of:

```
ifconfig
```

in your next post.

Jim

The output of ifconfig is:
lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:3544 (3.5 KB)  TX bytes:3544 (3.5 KB)

---

