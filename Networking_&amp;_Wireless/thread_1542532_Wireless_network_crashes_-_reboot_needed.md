---
title: "Wireless network crashes - reboot needed"
date: 2010-07-30
forum: Networking &amp; Wireless
---

### Post by G_u_s on 2010-07-30
Dear all,

I'm using Lucid 64 Desktop on a MacBook 2.1.

Wireless worked out of the box, but sometimes, wireless will crash for no apparent reason. The network manager will then try to reconnect to the network, but instead of connecting automatically with the saved key, it will ask again for it. Then after entering the key, it will try to connect for a while, and pop up the window to enter the key again. Only a reboot fixes this, log-out or ctrl-alt-backspace don't work.
It happens about once per day, but I could discern no pattern: sometimes i will not notice it happening, and just now, it crashed twice in the past hour, hence prompting me to write this post =)

Ideas and suggestions are welcome. A handy workaround would be to give me the commands that restart networking completely, so that i don't have to reboot every time. Thank you!

---

### Post by G_u_s on 2010-07-31
Bump. Anyone has an idea? It just happened again, and it's very frustrating...

---

### Post by G_u_s on 2010-08-01
Please, someone must know =( This is supposed to be a stable version, and plenty of stuff is not stable...

---

### Post by G_u_s on 2010-08-05
Any idea at all...? =(

---

### Post by G_u_s on 2010-08-06
Seriously...? I'm not even asking for a solution to the underlying problem, I'm just asking for a command... =(

---

### Post by cgb on 2010-08-06
Have you used the MacBook on any other network?  Do you have the same problems attaching to other wireless networks?  Just curious if maybe the problem is related to the router.  You could try the below command and see how that works for you to restart the wireless connection...

```
ifconfig wlan0 down
```

then follow with

```
ifconfig wlan0 up
```

see if that brings back life next time it happens...

---

### Post by G_u_s on 2010-08-07
> **cgb said:**
> Have you used the MacBook on any other network?  Do you have the same problems attaching to other wireless networks?  Just curious if maybe the problem is related to the router.  You could try the below command and see how that works for you to restart the wireless connection...

```
ifconfig wlan0 down
```

then follow with

```
ifconfig wlan0 up
```

see if that brings back life next time it happens...

I have used it in other places, but not long enough to be sure if it is my router, or the MacBook, or a combination of the two (this specific router causing a particular bug to happen).

Next time my network crashes, I will try this, although I suspect it won't be enough: when it happens, I have to restart the computer, logging off and on doesn't work. But at least I have something to try out.

THANK YOU, very very much.

---

