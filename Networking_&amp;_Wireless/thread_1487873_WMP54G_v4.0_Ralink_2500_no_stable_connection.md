---
title: "WMP54G v4.0 Ralink 2500 no stable connection?"
date: 2010-05-19
forum: Networking &amp; Wireless
---

### Post by mk13139 on 2010-05-19
I have a wmp54g v4.0(ralink 2500).
After I installed Ubuntu 10.04 the wmp54g was recognized, but it didn't find any networks. So I installed the windows driver in ndiswrapper (rt2500.inf and rt2500.sys).
Now I was able to connect to my network, but every time I tried to access the internet or download something the wmp54g stopped working and lost connection, and auto reconnected afterwards.
When it was connected, I still had 65 % signal strength, so no signal problems.

Am I doing something wrong? How can I get the wmp54g properly installed?

I use WPA + TKIP b.t.w.

---

### Post by mk13139 on 2010-05-19
Never mind, I solved the problem.
 
It turned out my antenna was to big for the wmp54g, so I fitted a 2dbi one instead of 7dbi.
 
Now I have a good connection!

---

