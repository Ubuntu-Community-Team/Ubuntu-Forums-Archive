---
title: "Unable to play DVDs"
date: 2014-04-18
forum: Multimedia Software
---

### Post by rachel-g41 on 2014-04-18
Lubuntu 13.10

I've just tried to play a DVD for the first time on this laptop and it isn't recognised. 

I've looked at various threads and tried installing libDVD.... but still no luck. VLC tells me it can't read the DVD and can't read the MRL.

Thinking it would be a problem with region (my DVDs are region2 and I recently bought a new laptop in S America which I suspect is Region 1 ?) I tried installing regionset. However when I run it, it tells me 

[B]ERROR: Could not open disc "(null)"!
Please ensure there is a readable CD or DVD in the drive.[/B]

Can anyone suggest anything else I can try please?


Edited to add, having read further am installing ubuntu restricted extras - fingers crossed

---

### Post by rachel-g41 on 2014-04-18
No, no luck still can't play DVD or run regionset. 

Advice please!

---

### Post by rachel-g41 on 2014-04-18
It's working! Stupidest stupidest problem, the path VLC was looking at wasn't correct, browsing for a correct path has solved the problem

(Although strangely, VLC is confused about what disk I have in - I tried a couple to see if it was a disk problem, it showed me the menu for the first while the 2nd was in and is playing.....)

---

### Post by ibjsb4 on 2014-04-18
libdvdread4 ?

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Installing_libdvdcss](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Installing_libdvdcss)

---

### Post by rachel-g41 on 2014-04-18
Thanks, yes, that was one of the bits I installed - it just didn't work until I got the path set correctly. 

All's well that ends well.

---

