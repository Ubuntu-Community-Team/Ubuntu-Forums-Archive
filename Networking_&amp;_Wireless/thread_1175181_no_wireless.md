---
title: "no wireless"
date: 2009-05-31
forum: Networking &amp; Wireless
---

### Post by cslsr on 2009-05-31
Ok, I have searched the forums trying to find my problem specifically, but I'm new to this Linux thing, and cant seem to track it down.
 
I installed Ubuntu 8.1 today on my laptop. It is now not connecting to the internet. I have windows XP Pro on my desktop, and thats where my wireless network is set up. The little blue indicator light won't even come on on the laptop. I know whomever reads this will need more info, but I need specific instructions on how to locate this info because like I said, I'm new to this.

---

### Post by Ayuthia on 2009-05-31
Welcome!  Can you go into the Terminal and post the results of:
```
lspci -nn
```It will help us see what wireless card you have.

If you don't have an internet connection in Ubuntu, can you find out what wireless card you have in XP or else can you give us the make and model of your laptop?

---

### Post by cslsr on 2009-05-31
I have an HP pavilion dv4000. Intel PRO/wireless 2200BG

---

### Post by Ayuthia on 2009-06-01
From what I can tell, it should work in Ubuntu.  You might first check (from the Terminal):
```
sudo iwlist scan
```to see if you are able to see any wireless sites.

If you can't, please post the results of:
```
lshw -C network
```

You might also check any information in dmesg:
```
dmesg
or
dmesg|grep ipw
```Hopefully there will be some clues in there about your wireless.

---

