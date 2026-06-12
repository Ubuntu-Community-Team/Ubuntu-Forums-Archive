---
title: "Internet connectivity"
date: 2010-07-13
forum: Networking &amp; Wireless
---

### Post by ZX81Overclocker on 2010-07-13
I am relatively new to Ubuntu.  Currently running Lucid Lynx, but I  cannot connect to the internet.  I can ping 127.0.0.1, and google.com.   Software update works as well, but the connection times out when I try  connecting to a web site eg bbc.co.uk

---

### Post by ZX81Overclocker on 2010-07-13
Forgot to add, I can also download and install software from the Ubuntu software centre as well

---

### Post by Tech2077 on 2010-07-13
Can you install software, and type 'lynx [www.ubuntu.com](www.ubuntu.com)' in your terminal and if it displays the text of ubuntu.com, it may be another problem

---

### Post by ZX81Overclocker on 2010-07-13
All I get is :-
Alert!: Unable to connect to remote hoste

---

### Post by ZX81Overclocker on 2010-07-14
Think I have solved this problem.  I installed the Chrome web browser, and was able to connect to the internet successfully.  This lead me to think that it was a Firefox issue, as I was trying to access the web via FF.  I did  a search on this forum, and found a solution which works for me.  Basically, I did :-
1 In the FF address bar, enter about:config
2 In the filter bar, enter ipv6
3 alter the **network.dns.disableIPv6** value to true

More details in here, [http://ubuntuforums.org/showthread.php?t=1522409&highlight=firefox](http://ubuntuforums.org/showthread.php?t=1522409&highlight=firefox)

Thanks to Barry_IA, and t3ubu

---

