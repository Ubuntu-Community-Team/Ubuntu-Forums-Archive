---
title: "Loading modules"
date: 2009-04-09
forum: Networking &amp; Wireless
---

### Post by Brian_ on 2009-04-09
Hi, I own a Dell Inspiron 1720 and I'm having problems with my wireless card. When I turn it on, the wireless card starts disabled (the light is off on startup)

I found searching in the forum a way to make it work.

Each time I turn on the computer I have to do the following:

rmmod b44
rmmod ssb
rmmod wl
modprobe wl
modprobe ssb
modprobe b44

And everything works ok.(the wireless light turns on and I can use internet fine)

I want to make it load automatically, but I could find anything.

I'd appreaciate any help, thanks in advanced

---

### Post by Brian_ on 2009-04-10
If it's posted in the incorrect section just tell me where to put it :)

---

### Post by chili555 on 2009-04-10
> rmmod b44
rmmod ssb
rmmod wlWhen you turn on the computer and the wireless doesn't work, are these three actually loaded? What does this report:```
lsmod | grep b44
```You could try adding the sequence to */etc/rc.local* on six separate lines, just above *exit 0*.

---

### Post by Brian_ on 2009-04-10
> **chili555 said:**
> When you turn on the computer and the wireless doesn't work, are these three actually loaded? What does this report:```
lsmod | grep b44
```You could try adding the sequence to */etc/rc.local* on six separate lines, just above *exit 0*.

lsmod reports:

[I]b44                    41872  0
ssb                    46340  1 b44
mii                    14592  1 b44
[/I]

Adding the six lines of the first post to rc.local worked.
Thanks

---

