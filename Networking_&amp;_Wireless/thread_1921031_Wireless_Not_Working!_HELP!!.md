---
title: "Wireless Not Working! HELP!!"
date: 2012-02-05
forum: Networking &amp; Wireless
---

### Post by VIK96T on 2012-02-05
I just got a computer well over 5 years old. Its a compaq Presario V4000 and I fully installed ubuntu 10.04 onto it. However the wireless hard button will not light up when clicked so the computer cannot connect/search for networks? what do i do??


ps. sorry if i posted in the wrong thread i am new to this and i will gladly move it if i did.

---

### Post by madvinegar on 2012-02-06
First of all open a terminal and write

```
lspci
```

and post the results.


Have you tried going to additional drivers and see if there is any recomended driver available for activation for your wifi card? (You would have first to plug an ethernet cable on your PC so as to get internet and update all the packages in synaptics).

---

### Post by varunendra on 2012-02-06
Hi VIK96T, Welcome to the forums!
> **VIK96T said:**
> ps. sorry if i posted in the wrong thread i am new to this and i will gladly move it if i did.
Don't worry about that, I've already requested the mods to move it to the 'Networking' section. (you can't move a thread anyway :))

As for the problem, the outputs of the following commands would provide us some detailed info about the network cards and setup:
```
lsb_release -a
uname -mr
lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
iwconfig
rfkill list all
```
Please wrap the outputs in [ code] ..and..  [ /code] tags by clicking on the **# **symbol  at the top of the edit box (in which you create new posts) to generate  those tags, the copy-paste the output code in-between those tags. It'll  preserve its formatting and make it easily readable.

---

### Post by nothingspecial on 2012-02-06
*Thread moved to **Networking & Wireless**.*

---

