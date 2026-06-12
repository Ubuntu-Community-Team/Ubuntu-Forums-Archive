---
title: "recommended hardware for laptops?"
date: 2006-10-17
forum: Multimedia &amp; Video
---

### Post by amityadav on 2006-10-17
hi. i'm looking for something for laptop which won't have latency issues.. i am using dell m 140 which has an express card slot but doesnt support pcmcia. can anyone suggest me an audio express card? i have looked around and cant seem to find one.
a lot of usb interfaces are available but i am not sure about the latency issues... and it looks like firewire interfaces are not generally well supported in ubuntu.... so what can be a good  option for me? 
thanks!

---

### Post by hendrikwout on 2006-10-25
A standard usb audio interface should work (you should ask in the store whether it needs extra software to be installed in Windows, if it doens't, it will work in also ubuntu).


Here my succes story:
I bought the little **imic** in an apple store and works very well with ubuntu. It wasn't cheep, (40 euro's), but now I think think it's worthed. it has decent audio quality and works with **jackd** (the command jackd -d oss -C /dev/dsp -P /dev/dsp -n 16 -p 32 -r 44100). It doesn't have midi.

---

