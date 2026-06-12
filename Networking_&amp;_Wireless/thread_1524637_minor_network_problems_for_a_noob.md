---
title: "minor network problems for a noob"
date: 2010-07-05
forum: Networking &amp; Wireless
---

### Post by blackmail on 2010-07-05
Ok ppl, i have a routed and a PPPoE type internet connection, recently i tried a thing in terminal with the pppoeconf option since the network manager has problems with connectiong to the internet with a pppoe DLS connection, or anyway in my case it does not work. Ok i did the pppoeconf thing i inserted my pass and my user and left the program to do its thing, ok it all worked fine but then i restarted my system and suddenly the network manager did not want to recognize my network it hat as options some weird ipupdown options for connection and when i tried the pppoeconf thing again it did not work. what could i do to reactivate at least one way my connection, if i understood correctly the terminal type connecting and the network manager are two different things. So could i please get some help regarding this issue, now i am using my router and it should connect but the network manager still does not see the connection. i just want it to work... I HAVE EXAMS TOMORROW

---

### Post by carsonrose on 2010-07-05
> **blackmail said:**
> Ok ppl, i have a routed and a PPPoE type internet connection, recently i tried a thing in terminal with the pppoeconf option since the network manager has problems with connectiong to the internet with a pppoe DLS connection, or anyway in my case it does not work. Ok i did the pppoeconf thing i inserted my pass and my user and left the program to do its thing, ok it all worked fine but then i restarted my system and suddenly the network manager did not want to recognize my network it hat as options some weird ipupdown options for connection and when i tried the pppoeconf thing again it did not work. what could i do to reactivate at least one way my connection, if i understood correctly the terminal type connecting and the network manager are two different things. So could i please get some help regarding this issue, now i am using my router and it should connect but the network manager still does not see the connection. i just want it to work... I HAVE EXAMS TOMORROW

Get rid of the network manager altogether and assign your IP and gateway manually....

sudo vim  /etc/network/interfaces then reboot.....

---

### Post by dineshs on 2010-07-08
pl try this
[http://ubuntuforums.org/showpost.php?p=9554325&postcount=5](http://ubuntuforums.org/showpost.php?p=9554325&postcount=5)

---

### Post by blackmail on 2010-10-18
thnx ppl, this seems to have solved my problems!

---

