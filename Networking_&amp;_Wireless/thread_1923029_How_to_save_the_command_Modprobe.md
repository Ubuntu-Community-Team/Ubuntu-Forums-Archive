---
title: "How to save the command Modprobe?"
date: 2012-02-09
forum: Networking &amp; Wireless
---

### Post by bengeijtenbeek on 2012-02-09
Hello Ubuntu fans, I have a newbe problem i like to get solved.
I found a solution in this forum. That is by typing "modprobe rt2800usb" Now my wireless usb stick starts working just fine.
Bud... i have to type it everytime i startup my pc. 
Where/how do i save this info so that it starts up automatic.

Thanks ... Ben

---

### Post by shakabra on 2012-02-09
I believe you can but the command into your /etc/rc.conf. This file is run everytime you startup. However you may have to also put it into a script in /etc/pm/suspend.d to get it to run when you resume from suspend.

---

### Post by bengeijtenbeek on 2012-02-10
I use Ubuntu 10.4 lts. 
I cant find a "rc.conf" file in the directory etc ?
Do i have to make it?
Thanks for ure answer anyway!

---

### Post by nothingspecial on 2012-02-10
Hi, to load a module at boot you put it in /etc/modules

Just a single line at the end

```
rt2800usb
```

It doesn't need modprobe in front of it.

Be careful when you edit it.

---

### Post by bengeijtenbeek on 2012-02-10
Thank u! That was what i was searching for!

---

### Post by nothingspecial on 2012-02-10
You are welcome :)

Next time you resolve an issue on the forums, please mark your thread as solved using the thread tools button at the top of the thread.

I've done it for you this time.

---

