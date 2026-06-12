---
title: "how do i enable my wireless through terminal?"
date: 2011-05-26
forum: Networking &amp; Wireless
---

### Post by DividedSky on 2011-05-26
i have jolicloud (i think it uses gnome) on my hp mini 110 and my internet has been working fine and everything until for some dumb reason i pushed the wireless on/off button on the front of the computer. normally on windows i would just have to push the button again but its not working with linux. how can i re-enable my wireless?

---

### Post by DividedSky on 2011-05-26
rfkill list

0: brcmwl-0: wireless lan
soft blocked: yes
hard blocked: yes
1: hp-wifi: wireless lan
soft blocked: yes
hard blocked: no
2: hp-bluetooth: bluetooth
soft blocked: yes
hard blocked: no

---

### Post by DividedSky on 2011-05-26
i did "sudo rfkill unblock all" and my rfkill list is now:


0: brcmwl-0: wireless lan
soft blocked: no
hard blocked: yes
1: hp-wifi: wireless lan
soft blocked: no
hard blocked: no
2: hp-bluetooth: bluetooth
soft blocked: no
hard blocked: no
4: hci0: bluetooth
soft blocked: no
hard blocked: no

______________

Awwwwww yeah it works baby

---

### Post by josephmills on 2011-05-26
```
rfkill unblock all 
``` and could we see a ```
lsmod
``` also what kind of computer is this?  thanks

---

### Post by DividedSky on 2011-05-26
Solved

---

### Post by jawilljr on 2011-05-26
> **DividedSky said:**
> Solved

How?

---

### Post by MSPdwalt on 2011-05-26
> **DividedSky said:**
> Solved

Don't forget to go to thread tools and mark as solved.  I can't wait to test this on my Dell.  I did that once and I had to disable it in the BIOS, boot up, shut down, and re-enable it in the BIOS.

---

### Post by josephmills on 2011-05-26
I think that it was because it was softblocked so when he would turn the wifi switch it would do nothing now that he did a rfkill unblock all that stopped the soft block then all that needed to happen was to turn the wifi switch now I wonder what will happen on reboot ?

---

