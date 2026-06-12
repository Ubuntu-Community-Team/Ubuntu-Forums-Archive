---
title: "Realtime Bandwidth Monitoring"
date: 2010-03-15
forum: Networking &amp; Wireless
---

### Post by safelinux on 2010-03-15
Hi,

I want a bandwidth monitor which performs constant monitoring of the ethernet.

I want to see how much bandwidth I am spending by opening each website, downloading, etc.

A small program which can remain "always on top".

I am using Gkrellm but the problem is it does not updates itself constantly, I mean I have to close/open its eth0 monitoring window to view changes (I am not talking about restarting Gkrellm, only the bandwidth window which shows the daily, monthly bandwidths).

Please help.

---

### Post by safelinux on 2010-03-19
Nobody ???

---

### Post by Fafler on 2010-03-19
I would like to see that too. A program that automatically chooses the interface choosen as default gateway, because i use several different interfaces for internet access depending on where i'm at and what i'm doing.

---

### Post by Grenage on 2010-03-19
The only thing I have used is *[netspeed]("http://www.howtoforge.com/keeping-an-eye-on-your-internet-speed-with-netspeed-gnome-ubuntu-8.04")* (applet) but there are plenty of other utilities.

---

### Post by Fafler on 2010-03-19
Exactly what i was looking for. Thanks!

---

### Post by safelinux on 2010-03-19
Thanks for your replies.


I just found out about this screenlet.

Go to synaptic & install screenlets.

The default installation of screenlets includes "NetMonitor".

It can remain "always on top".

It updates itself in realtime.


I will try netspeed.

Thanks again.

---

### Post by jrssystemsnet on 2010-03-19
It's not particularly pretty (text mode only), but you might also have a look at nethogs.  (It's in the repositories.)

---

### Post by doas777 on 2010-03-19
on local host, I usually use iftop (in repos) to track usage to each process. if i need it net wide though, I have to go to my routers ntop reports.

---

