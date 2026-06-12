---
title: "PPPoE via Wireless"
date: 2009-11-13
forum: Networking &amp; Wireless
---

### Post by shawnerz on 2009-11-13
Hello all.
I am running the 64 bit version of Ubuntu on a Gateway MX6421 laptop.  I'd tell you the exact version of Ubuntu I'm running, but I had to boot to WIndows in order to get to the Internet.

My local ISP changed from running PPPoE over a cabled connection, to PPPoE over a wireless connection.  When the service was provided over a cable, I managed to go to Network Connections | DSL tab, and enter to login information there. I must have done it correctly, because it just magically worked.
Now that I have to use the wireless interface, I can't get the PPP login to work.

I seached the forum here and found a reference to changing the interface listed in pppoed.  I did a 'locate' to find pppoed and couldn't find the file.  I did find pppd, but it was no help.  I also looked for corresponding .conf files.

How do I get the ppp login to work over iwlan0?
Thanks in advance,
-Shawn

---

### Post by shawnerz on 2009-11-15
I found the answer to my question.  I happened to stumble across a couple man pages that steered me in the right direction.
To configure PPPoE over the wireless adapter, open **Terminal**.
At the prompt, enter **sudo pppoeconf iwlan0** or whatever the name of your wireless interface happens to be.
You will be presented with a GUI and a series of questions.
The defaults worked for me.:D
-Shawn

---

### Post by shawnerz on 2009-11-17
I just wanted to add a couple of things:
1: I'm running the 64 bit version of 9.04 (Jaunty).

2: In this version, when pppoeconf is run and configured, you will loose the wireless status indication in the top right of the display.  It's kind of a downer because the visual indication is a quick indication if your internet connection is still up or if it has dropped. :(

---

### Post by trelozakinthinos on 2010-05-23
Hello from Poland...
I have the same problem in my dormitory.
I can connnect to the access point but i couldent connect to the thing that i'm supposed to put username and password. So i found the pppoeconf.
It didn't work for me and i also lost the wirelees indication.
Is it possible to bring it back?????
And the most important how can i connect to pppoe>?
Pls help!

A desperate greek student in Poland!:popcorn:

---

