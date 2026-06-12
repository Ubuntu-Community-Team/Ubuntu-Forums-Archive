---
title: "[SOLVED] using windows xp laptop wireless to conect ubuntu"
date: 2009-01-04
forum: Networking &amp; Wireless
---

### Post by matthewbrave on 2009-01-04
evening all,

i have just installed 8.04 on another computer. since there is no wireless card in this machine i was wondering whether i could connect it to my windows xp laptop via a network cable and configure it all so that i can still use the internet on my laptop and use ubuntu on the internet as well.


is this possible in some way??



thanks

---

### Post by matthewbrave on 2009-01-04
after a bit of searching i found a thread that helped me.

for anyone with the same problem visit this address:

[http://ubuntuforums.org/showthread.php?t=101011](http://ubuntuforums.org/showthread.php?t=101011)


this might help you!!

---

### Post by Zebra_ on 2009-01-04
Yes this is possible, however you will need an ethernet crossover cable rather than a normal ethernet cable. Go to Start>Control Pannel> Network Connections, and then find "Local Area Connection" and "Wireless Internet Connection".right click on either, and select Properties>Advanced, and under the "Internet connection sharing", make sure nothing is checked (do this for both the Wireless and the Local connections). Then go back to the Network Connections window, and hold down the "Ctrl" key. Click both the wireless connection, and then the local connection. When you have them both highlighted, right click on either one of them, and select "Bridge connections" Wait while the system does this for you, and once the connection bridge appears, you should be all set.

---

### Post by superprash2003 on 2009-01-05
please mark thread as SOLVED under thread tools

---

### Post by matthewbrave on 2009-01-07
i now have the crossover cable, i have tried bridging the connections but nothing happened.

---

### Post by matthewbrave on 2009-01-07
it doesent matter now, after a bit of tinkering i got it to work

---

