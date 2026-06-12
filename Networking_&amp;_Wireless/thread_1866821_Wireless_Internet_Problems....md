---
title: "Wireless Internet Problems..."
date: 2011-10-22
forum: Networking &amp; Wireless
---

### Post by niksmc on 2011-10-22
Hello there! I know you guys are probably going to be like, "you lazy b***h go look this up for yourself." 
BUT, I have tried and tried and amazingly failed at understanding anything whatsoever. I am new to ubuntu. I installed it on a whim thinking that it would be okay, and it has been. It's awesome! I love ubuntu! There's just one problem, I can't figure out how to get my laptop to connect wirelessly. Everything I read is like, go download this, and install this, and go to your computer input thingy and type in <=su input hjsaa fdhsjfhs4443245325> or something like that and I'm like I DON'T KNOW HOW!?!?! :confused:

If anyone has any suggestions that can be understood by a total nooooooob, please send them this way. Thank you very muuuuch! 
With hearts, hearts and love, 
Nikki

---

### Post by kurt18947 on 2011-10-22
A nice first step might be to post the output of these terminal commands:
```
lspci
```  
and
```
lsusb
```

This will tell us what kind of wireless adapter you have. What we're looking for is something like this:
```
Bus 002 Device 002: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191S WLAN Adapter
```

---

### Post by niksmc on 2011-10-22
Do what? I don't even know how to get to terminal commands

---

### Post by vasa1 on 2011-10-22
> **niksmc said:**
> Do what? I don't even know how to get to terminal commands

Press the control **and** alt keys **and** the key for the letter t briefly **but** all together and let go.

---

### Post by niksmc on 2011-10-22
> **vasa1 said:**
> Press the control **and** alt keys **and** the key for the letter t briefly **but** all together and let go.

Okay. If I do that how can I get back to my desktop? What am I looking for? What do I type? I seriously know nothing about this. I don't want to get in there and mess up something...

---

### Post by Al-amin on 2011-10-22
i tried all the commands, but didnt work... it does not detect any wlan adapter. im using dell xps.. L502X.... please help

---

