---
title: "i'm a noob with a problem."
date: 2010-04-22
forum: Networking &amp; Wireless
---

### Post by dclantz on 2010-04-22
I just got Ubuntu and i feel like there is going to be a really simple solution but right now i cannot find any information on a solution. I run 9.10 desktop i386 or w/e and i have a wireless connection. The network does not show up when i go the network manager to select a network. no networks show up and all it lets me do is create a new network connection which i have no idea how to do. I think it might have to do with my device recognition, but the network is fine it is just Ubuntu. Your help would be greatly appreciated. thank you

---

### Post by qixil on 2010-04-22
Yes - I tried messing with that icon in the top-right when I had network problems.

I suspect that you're having problems with your wireless driver - I've found Mr google very helpful in this regard. Find out what your wireless device is and do a search.

Worked for me...

---

### Post by bobyy on 2010-04-22
Hy ,,firt see if you`r wirelless switch(if you have a laptop)is enabled...i mean the physical oane.
After that see if apears like device in 
copy paste this command here:
#lspci

---

### Post by bobyy on 2010-04-23
Well .. any news ???

---

### Post by Iowan on 2010-04-23
From a terminal (Applications>Accessories>Terminal):
```
sudo lshw -C network
``` This should provide information about your interfaces. Post results (if possible) - more details if you need them.

---

