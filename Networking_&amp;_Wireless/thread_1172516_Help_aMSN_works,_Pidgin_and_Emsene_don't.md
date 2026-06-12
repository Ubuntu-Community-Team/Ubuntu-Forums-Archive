---
title: "Help aMSN works, Pidgin and Emsene don't"
date: 2009-05-28
forum: Networking &amp; Wireless
---

### Post by MattWong on 2009-05-28
Hi all,
I'm a new Ubuntu and Linux user, so apologies in advance if I posted in the wrong forum, or forget to include some information

So here's my problem
I recently (2 days ago) installed Ubuntu 9.04 on my HP 2133 mininote laptop.
Everything worked out of the box, I only had to enable the broadcom wireless driver to get the internet working (I was very pleased with how easy the install was btw, great job Ubuntu team)
Right from the start pidgin worked and I was able to sign in using my gmail windows live account

Yesterday, I attempted to try emesene and after installing I couldn't login. The emesene window would go all gray and after a LONG while would give me a login error: [Errno 104] Connection reset by peer
(attempting to close before this error appeared would tell me that emesene was not responding and asked if I wanted to wait or kill it)
when I tried to go back to pidgin it wouldn't work either, it would also hang while connecting and would eventually give me a connection fail message (I don't remember the exact message) but it mentioned Read Error at the end.

meanwhile since I'm dual booting with windows, msn live messenger is working, so its not msn server side (I think)

Finally today, I gave aMsn a shot and it works, but I don't like the interface that much, so I'd like to try emesene or go back to pidgin.


any ideas or suggestions?

Thanks in advance
Matt

---

### Post by Tibuda on 2009-05-28
For pidgin, you could install the msn-pecan, which allows you to connect Pidgin to MSN using an alternate protocol (WLM).

---

### Post by MattWong on 2009-05-28
I installed msn-pecan, same issue, though I didn't wait long enough to see if the error message appeared. But for sure pidgin wasn't signing in.

The internet works, so I've assumed that it wasn't the problem

but I tried downloading something and now noticed that downloading is quite slow, could my wireless device/connection be to blame?

if so, what kind of logs/info should I post to help diagnose?

---

### Post by Tibuda on 2009-05-29
Have you created a new account with the WLM protocol? When you install msn-pecan, you have two "butterfly" protocols available: the default MSN, and the WLM installed by msn-pecan. You have to create a new account with this new protocol.

I would check your wireless connection too. I can't help you with this very much. Are you using ndiswrapper?

---

### Post by MattWong on 2009-05-29
oh, I didn't notice the WLM option, Pidgin works now! 
thanks a lot!

emesene still doesn't work though, but I'm happy with pidgin for the moment

thanks again

---

