---
title: "Command to turn on wireless reciever?"
date: 2011-06-18
forum: Networking &amp; Wireless
---

### Post by winslowevan on 2011-06-18
[IMG]http://postimage.org/image/33d40mih0/[/IMG]My wireless is stuck off, i put the command rfkill list and it says
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
How do I unblock it?[IMG]http://postimage.org/image/33d40mih0/[/IMG]

---

### Post by winslowevan on 2011-06-18
Well I am officially an idiot, all I had to do was go in terminal and say rfkill unblock wireless 0: Lan or something of the sort, If you need to know how to do this just ask me.:lolflag:

---

### Post by dFlyer on 2011-06-18
Please mark this as SOLVED.

---

