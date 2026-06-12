---
title: "Trouble connecting to wireless internet"
date: 2009-07-08
forum: Networking &amp; Wireless
---

### Post by lotster on 2009-07-08
Hi!

I'm trying to help a friend set up his internet using Ubuntu (I'm trying to convert him from Windows).  His setup is fairly complicated, but let me explain.

His ISP is a company that broadcasts ADSL signals wirelessly; so he connects to their tower using a normal wireless network card.  Then, after connecting to the network, he uses PPPOE with a username and password to connect to the internet over the wireless network.

Then he shares this internet connection with his family through a standard cable ethernet connection.

What I want to know is, how can we set that up for him using Ubuntu 9.04?  I tried to connect to the wireless network, but though it detects the tower, it doesn't connect.  I read something about it having to "brute force", or something like that, but I can't find any further info on Google.

I would appreciate any help...  Thanks!

---

### Post by lotster on 2009-07-10
Nobody have any ideas?

---

### Post by superprash2003 on 2009-07-10
try getting outputs of
1)iwconfig
2)sudo iwlist scanning
3)ifconfig 

to know where exactly the problem lies..

---

