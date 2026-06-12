---
title: "Dial-up problems"
date: 2005-12-30
forum: Networking &amp; Wireless
---

### Post by Roger Hunter on 2005-12-30
Hi all;

I'm an old programmer but new to Linux. I've tried Mandrake, Knoppix and now Ubuntu.

I have an AMD Athlon system with 512MB RAM running Win98 and Linux in separate partitions on a 40Gb HD.

The problem is the modem. It's an external 56k and I managed to get it working after a couple of days. Rather, the problem was connecting to the Internet. When set up under network it was always on. ISPs don't like that. Finally discovered Modem Lights and was able to turn it on and off, but the browser couldn't see it. 

Now it's connected to the network again and Modem Lights can still control it.

What a hassle. No wonder Linux isn't catching on as a desktop.

Roger

---

### Post by Stereotypical Rage on 2005-12-30
Most of the people who use Linux in my experience, use Broadband.

---

### Post by towsonu2003 on 2005-12-30
[QUOTE=Stereotypical Rage]Most of the people who use Linux in my experience, use Broadband.[/QUOTE]
most people in the US maybe but it's also the driver problems stopping pple using it with dialup  (you know, the winmodem thing)... you're very lucky to get it working in a couple of days though...

as for the dial up issue you have, I am not sure if I understand correctly but, you could try wvdial to control your dial up actions (connect and disconnect). 
```
sudo apt-get update
sudo apt-get install wvdial
man wvdial
sudo wvdialconf /etc/wvdial.conf
sudo gedit /etc/wvdial.conf
sudo wvdial
```

1 & 2 to install; 3rd to read about it; 4th to set it up (is supposed to see your modem during set up); 5th to put in your isp details; 6 to dial up and connect (do not close terminal)

ctrl+c to disconnect

linux isn't catching with desktop bc. ppl are addicted to MS + everything being too easy (no need to do anything but press buttons) + lack of proper drivers from hardware manufacturers... you'll get used to linux in 2-3 months...

good luck and enjoy.

---

### Post by Roger Hunter on 2005-12-30
Broadband?

I wish! $100/month for satellite where I live.

Not on MY retirement.

Roger

---

### Post by linuxguiri on 2005-12-30
Roger,

Just saw your post about Modem Lights. I've been trying to get the dial-up working on Ubuntu (5.10 Breezy Badger) for the past 3 days.

I would really appreciate it if you would tell me how you set it up. 

And where did you find Modem Lights? 

Thanks!

---

### Post by towsonu2003 on 2005-12-30
[QUOTE=Roger Hunter]Broadband?
Not on MY retirement.
Roger[/QUOTE]
lol
same with a student's income (=$0)
any luck with wvdial, if I understood your problem correctly?

---

