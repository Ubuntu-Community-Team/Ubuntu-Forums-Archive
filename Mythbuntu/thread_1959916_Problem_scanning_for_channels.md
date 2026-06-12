---
title: "Problem: scanning for channels"
date: 2012-04-16
forum: Mythbuntu
---

### Post by Cons on 2012-04-16
Hello everyone, 

I do not get the tv running. I am using a clean installation of mythbuntu 11.10 and TT DVB-S2 3200. I can not scan for channels (using: frequency 12551000, rate: 22000000 and polarity: Vertical) but got immediately the result: “Failed to find any channels”. 
I can do “scan /usr/share/dvb/dvb-s/Astra-19.2E > channels.conf” with reasonable results but I can’t load this file (same message). 

Maybe the problem is here: 2. Capture cards -> MyCard -> DiSEqC -> unconnected and here I can not change anything. I assume I have to add here some values about my LNB or am I wrong? 

Kaffeine is working at this installation, so hardware must be ok.

Anyone can give me a hint?

Thank you for your help (and thank you for reading to the end of this post). 

Best regards 
Cons

---

### Post by Cons on 2012-04-19
No one with a hint?

```
Maybe the problem is here: 
2. Capture cards -> MyCard -> DiSEqC -> unconnected and 
here I can not change anything. I assume I have to 
add here some values about my LNB or am I wrong?
```

Maybe someone can answer this?

Best regards
Cons

---

### Post by Neon Dusk on 2012-04-19
Setting the DiSEqc option is notoriously buggy but should be possible - see [http://parker1.co.uk/mythtv_freesat.php](http://parker1.co.uk/mythtv_freesat.php)

---

