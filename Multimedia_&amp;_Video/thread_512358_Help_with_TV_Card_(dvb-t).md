---
title: "Help with TV Card (dvb-t)"
date: 2007-07-29
forum: Multimedia &amp; Video
---

### Post by nami on 2007-07-29
Hello,

I got a TV card (winfast dtv1000 t to be precise) and it is not working.

I bought this card based on the fact that it works "out of the box" on linux...

Please help as I do not know where to start even though I have done searching.  Maybe I am typing in the wrong phrase in google or something.

---

### Post by nami on 2007-07-29
I have recorded what I see when I try to scan for channels using mythtv.

Here is a link: [http://download.yousendit.com/87A75E75064F7E25](http://download.yousendit.com/87A75E75064F7E25)

When I connect the antenna to a normal tv it works...

---

### Post by nami on 2007-07-29
What does this mean?

> nami@nami-desktop:~$ grep -i dvb /var/log/messages
Jul 29 11:40:22 nami-desktop kernel: [   47.381826] cx2388x dvb driver version 0.0.6 loaded
Jul 29 11:40:22 nami-desktop kernel: [   47.381830] cx8802_register_driver() ->registering driver type=dvb access=shared
Jul 29 11:40:22 nami-desktop kernel: [   47.381837] cx88[0]/2: cx2388x based dvb card
Jul 29 11:40:22 nami-desktop kernel: [   47.418365] DVB: registering new adapter (cx88[0]).
Jul 29 11:40:22 nami-desktop kernel: [   47.418370] DVB: registering frontend 0 (Conexant CX22702 DVB-T)...
nami@nami-desktop:~$ 

---

### Post by ministoat on 2007-09-03
erm bump, i'd like to know if you got this working :)

---

### Post by nami on 2007-09-04
nope, i think it's a faulty card as it would not work on windows xp either when installed with the provided software.

i am waiting for a replacement.

---

