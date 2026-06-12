---
title: "TV7131 PCI TV card"
date: 2006-08-26
forum: Multimedia &amp; Video
---

### Post by Jungingen on 2006-08-26
Hi, i have a problem. I buy tv7131 card and i can't make it to work under linux. First off all, now i can't listen music - i'v got default xmms message "Couldn't open audio" . Also,  then i start tvtime-scanner, i'v got 

Scanning using TV standard PAL.
/root/.tvtime/stationlist.xml: No existing PAL station list "Custom".

    No tuner found on input 0.  If you have a tuner, please
    select a different input using --input=<num>.

Maybe you have some ideas?
thanks

P.S. sorry for english

---

### Post by Vladimir_BG on 2006-08-26
I had the same problem. Seems that the Philips didn't bother putting a chip that contains info on the card which is used for auto-detection. As a result Linux sees something but it doesn't really know what it is and loads wrong drivers. actualt, the right drivers with wrong parametars. You need to say what TV tuner you have(Model and manufacturer) first for us to help you.

---

### Post by Jungingen on 2006-08-27
All information i can find about my tv-tuner: 
Kworld Global TV Terminator
VS-LTV7131RF
TV7131 PCI TV Card
That's all information i found

---

