---
title: "Automatic Connection Sharing To The Xbox 360"
date: 2009-08-28
forum: Networking &amp; Wireless
---

### Post by fuzzman54 on 2009-08-28
I use my laptop for my Xbox's connection, and every time that I get on Live with my 360, I have to run this command

```
sudo ifconfig eth0 10.0.0.1
```and then start Firestarter (If I just start Firestarter without that command first it gives the error that "Eth0 is not ready"). It works fine, and I forwarded the ports and everything and now I even have an open NAT, but it is starting to be too much for my girlfriend to do when she wants to play. I made a shell script that ran the command above and started Firestarter, but is there any way to make it even easier? I mean, can I make it so that eth0 is always 10.0.0.1 and so Firestarter starts automatically when my Xbox turns on? Because when I turn my Xbox on, it says that the cable was disconnected and then I run the stuff and it works, but that means that the laptop knows when the Xbox is turned on, so I would think that I could make all of this automatic.

---

### Post by fuzzman54 on 2009-08-29
I've been looking around some more and found out that making eth0 10.0.0.1 would be done with iptables. How would I do that?

---

### Post by fuzzman54 on 2009-08-29
Nevermind, I figured it all out.

---

