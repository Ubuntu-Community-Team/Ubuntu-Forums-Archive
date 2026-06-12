---
title: "Where is my RT8111 driver?"
date: 2011-08-18
forum: Networking &amp; Wireless
---

### Post by Dyselinck on 2011-08-18
Yesterdag i managed to install the rt8111 drivers ( still don't know how, as i am a complete Noob :( )

So my ubuntu 11.4 started to download updates and after a reboot my internet failed again. I tried to do the same as yesterday but it failed.

If i look into lsmod i can't see the module listed.

Edit if i look into ifconfig Eth0 isn't listed :(

Can somebody help me (step by step )

Typing this from my w7 in another room.

Greets!

---

### Post by moaoci on 2011-08-18
Each time the linux kernel number changes during an update, my wifi driver has to be recompiled into the new kernel.  If you don't remember how you did it the first time, I suggest you write the commands into a text file  and save it on your desktop since you will most likely have to recompile again.

That's what I do for my wifi driver.

So the answer to your question is: Your driver is compiled into the previous linux kernel.  Just recompile it.(cd to the driver's file, sudo su, make clean, make, make install...)

That's all I can do...

---

