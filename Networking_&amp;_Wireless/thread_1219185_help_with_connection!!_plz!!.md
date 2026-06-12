---
title: "help with connection!! plz!!"
date: 2009-07-21
forum: Networking &amp; Wireless
---

### Post by rudra91 on 2009-07-21
hello people,
  recently i installed the latest version of ubuntu on my laptop, and enthusiastically brought a new modem as well. but the problems i faced are frustrating to baldness and havent found a solution yet.
1. to connect, a usermanual says system>administration> networking.
my problem> there is no networking, only network tools .
2. the laptop discovers a wireless network, but disconnects within 15 seconds.

what to do??!! please help!!

---

### Post by bacil on 2009-07-21
we need more info what modem ? can you see it in lshw ?

wirless is the same what wireless card ? are you using network manager ? can you send us output of 

```

iwconfig

```

and what is in your syslog in regards of network manager

---

### Post by rudra91 on 2009-07-21
my modem is ADSL (WA3002-g1). i tried everything, but nowhere did i get near to entering even my IP address. I may have missed something since i am new to this OS..

---

### Post by bacil on 2009-07-21
have look here here are some basics

[http://ubuntuforums.org/showthread.php?t=25557](http://ubuntuforums.org/showthread.php?t=25557)

adn this

[http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html](http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html)

---

### Post by rudra91 on 2009-07-21
Thank You..:D

---

### Post by rudra91 on 2009-07-21
eth1      unassociated  ESSID:off/any  Nickname:"ipw2100"

          Mode:Managed  Channel=0  Access Point: Not-Associated   
lo        no wireless extensions.



eth0      no wireless extensions.


          Bit Rate:0 kb/s   Tx-Power:16 dBm   

          Retry short limit:7   RTS thr:off   Fragment thr:off

          Power Management:off

          Link Quality:0  Signal level:0  Noise level:0

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:123   Missed beacon:0



pan0      no wireless extensions.

this is what i got on typing iwconfig

---

### Post by bacil on 2009-07-21
have you got all modules loaded  ? what is your network card ?

---

