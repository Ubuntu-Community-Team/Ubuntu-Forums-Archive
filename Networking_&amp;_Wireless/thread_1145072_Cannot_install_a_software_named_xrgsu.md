---
title: "Cannot install a software named xrgsu"
date: 2009-05-01
forum: Networking &amp; Wireless
---

### Post by permant on 2009-05-01
Hello
I am trying to install a software named xrgsu which could help linux system to connect to the local net.
In my installing process ,an error occured.

here is the message:


superman@ubuntu:~$ sudo cp libpcap.so.0.6.2 /lib
[sudo] password for superman: 
superman@ubuntu:~$ ./xrgsu -a
./xrgsu: /usr/lib/libstdc++.so.5: version `GLIBCPP_3.2' not found (required by ./xrgsu)
superman@ubuntu:~$ 



Could someone tell me what is the GLIBCPP_3.2 ,and how can I get the GLIBCPP_3.2.
I am appreciate your answer

---

### Post by chili555 on 2009-05-01
I wonder if it isn't really libstdc++5 that is needed.```
sudo apt-get install libstdc++5
```If it already installed, apt-get will tell you and post back so we can try again.

---

### Post by permant on 2009-05-02
Yes ,you are right!
when I install libstdc++5 as what you say ,It works!
Thank you!

---

