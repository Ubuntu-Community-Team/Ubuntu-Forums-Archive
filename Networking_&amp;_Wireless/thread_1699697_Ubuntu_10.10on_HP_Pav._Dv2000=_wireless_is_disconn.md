---
title: "Ubuntu 10.10on HP Pav. Dv2000= wireless is disconnected"
date: 2011-03-04
forum: Networking &amp; Wireless
---

### Post by Draggem on 2011-03-04
Urgent!

I have a Hp pavillion dv2000 and i installed Ubuntu 10.10 the wireless works really fine and fast until i decided to buy a windows vista and installed it, i didn't know that installing windows would affect other OS already installed, after installing vista I installed Ubuntu 10.10 again and the wireless wont detect anything and it would say on the wireless option 'discinnected'
and the wireless led light stays orange instead of blue.....
How do I fix this problem??
sorry but im a noob..

---

### Post by mounti on 2011-03-09
Also new,but I discovered that you have to enable bluetooth and wireless and leave it on in windows.Reboot to Linux,open terminal and use following command
 
   sudo rfkill unblock wifi

or 

   sudo rfkill unblock all

Hope it works!

---

### Post by Draggem on 2011-03-10
Thanks Mounti for a really good reply.
I really appreciate it and now I alguds with ubuntu...

---

