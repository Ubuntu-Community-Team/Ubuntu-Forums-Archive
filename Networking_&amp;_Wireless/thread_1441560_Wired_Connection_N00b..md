---
title: "Wired Connection N00b."
date: 2010-03-28
forum: Networking &amp; Wireless
---

### Post by TheWielder on 2010-03-28
So. On My computer, I used to have a wireless thing that needed a special program. I switched to Ubuntu, and the program no longer works. That's not the problem.

Problem is, now I'm trying to set up a wired connection. And, here's the Kicker... I'm a total n00b. I have no Idea what I'm doing, and need some assistance. I've looked all over the place, and come up short. I've got Broadband, and I've found the right cable type. I plugged it in, nothing happened.

All I know is that there's a Wired Connection called "eth0" and that I've filled in everything I can find on the 192.168.0.1 thing. If this kind of question has already been asked, or if you know where this is in a FAQ or something, please direct me to it. If you feel like telling me yourself, that's great too. I'll be checking often.

Thank you in advance.

---

### Post by dineshs on 2010-03-29
Do you have a modem connected via ethernet?

---

### Post by Aped on 2010-03-29
Once you plug that ethernet cable in, Ubuntu/Network manager should do all the rest of the work. Make sure you're connected with an 'ifconfig' - go ahead and paste the results of that here. Also: In the top right of your screen there should be a dropdown menu for your network manager. Make sure you have the wired network connection selected as active, so it isn't trying to connect through something else. 

Finally, do make sure that your modem or whatever you have the router connected to is active and working correctly. Once we know what's up in the ifconfig and the router/modem setup, the rest should be pretty straightforward. 

You shouldn't have to do anything in 192.168.0.1 or anywhere, unless you have some *very* odd settings enabled on your router/gateway.

---

