---
title: "I tried but I failed"
date: 2006-06-26
forum: Networking &amp; Wireless
---

### Post by loserboy on 2006-06-26
hey
i'm running ubuntu (dapper) at my house, but im trying to get it going at work

I've seen a bunch of howtos on getting a linksys wireless g pci working but appearently im a tard

1. do i need more than just ndiswrapper as far as programs go?

2. is there something i need to do before i install ndiswrapper, cuz i cant get it to install

(also i think its the rt2500 chipset)

thanks in advance

---

### Post by DarthMandeep on 2006-06-26
If it is a RT2500 chipset, it will work fine with Ubuntus native driver. You won't need ndiswrapper. Otherwise, ndiswrapper is pretty easy to install and use.

What exactly have you tried so far? Is the wireless card recognized, are you having trouble connecting to a specific access point?

---

### Post by tonyr on 2006-06-26
if it really is an rt2500 chipset, you shouldn;t have to do anything: There is an rt2500
wireless driver in the distribution.  To verify the chipset, In a terminal do
```

lspci | grep -i network

```

and see what it says.

---

### Post by loserboy on 2006-06-26
the network manager sees a wireless card but it doesnt tell me what it is, i dont know if that matters or not,  i can activate it but i still get no internet

maybe i'm not filling out everything properly, I really don't know how to configure it, i just tried what i do in windows, screw around until something happens.  lemme reboot back into it and get the info you asked

Edit: whoops  sorry guys  i had a missing letter from my Essid, the reason i didnt catch it was cuz i saw all these people with probs connecting. it works perfect sorry for the bother

---

