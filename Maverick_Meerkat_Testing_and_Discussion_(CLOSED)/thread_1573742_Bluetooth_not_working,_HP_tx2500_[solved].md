---
title: "Bluetooth not working, HP tx2500 [solved]"
date: 2010-09-13
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Gobe on 2010-09-13
I thought I put this up here, if some one else has same weird problem.

Computer: HP tx2500 AMD Turion x2 64, Ubuntu 10.10 beta

The bluetooth was loaded (modprobe and so on), and yet manager didn't start it. It just kept saying: "no devices available" As in no bluetooth chip. Tried to reload it with /etc/init.d/bluetooth restart etc, and no go.

Finally id did "rfkill list" and it showed: 

1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no

 so I gave it a "sudo rfkill unblock 2", and then "/etc/init.d/bluethooth start", and voila, now it works.

As I am totally n00b, I really cant say nothing on what I actually did, I do not know why that worked nor why it was blocked in the first place. Maybe it had good reasons for it, but I cant say =)  But now it works.

---

