---
title: "Is xsplash is working in Maverick Meerkat?"
date: 2010-06-06
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-06-06
i have installed xsplash and it was installed with no problem but i don't see that it's working at all at boot time all i see is an empty purple screen and that it.

I am using fglrx from here:
[https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates)

Thanks in advance.

---

### Post by autocrosser on 2010-06-06
I would say no--Ranchhand tried to make it work & I guess that it was less than a success. I'm sure he'll see this thread & give you the information.....

---

### Post by ranch hand on 2010-06-07
You are running on the plymouth splash.

That is what you are going to get as just about your whole system is dependent on libplymouth2 which is your boot manager.

If you are not having trouble booting and just do not like the splash screen, edit your /etc/default/grub file to not have "splash" in your boot command string.  This will give you a black screen for the few seconds it takes to get to the login screen.

There are plenty of threads telling you how to use the plymouth themes if you like and there are several themes around besides what is installed by default.  Several in a thread in the forum for 10.04-testing.

If, like me, plymouth is completely screwing your ability to boot and/or shut down you can go pound sand.

---

