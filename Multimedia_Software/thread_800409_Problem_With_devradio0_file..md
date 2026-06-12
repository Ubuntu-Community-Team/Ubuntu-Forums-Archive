---
title: "Problem With /dev/radio0 file."
date: 2008-05-19
forum: Multimedia Software
---

### Post by barcode_13 on 2008-05-19
Hey, 

Well I'm a little bit noob and as I was practicing my Ubuntu skills, I deleted radio0 file which is in (/dev).

Do you know any way to have it back. ? Now I am not able to listen to the radio.. :(:( 

Any help would be appreciated.! Thanks in advance :)

---

### Post by amingv on 2008-05-19
Try this:

```
sudo mknod /dev/radio0 c 81 64
sudo chmod 666 /dev/radio0
```

81 and 64 are approximate values I found with Google (you didn't provide any specifics), so they may not work, but that's the command you're looking for.

Also you may try reinstalling the card.

---

### Post by barcode_13 on 2008-05-19
Thanks A lot.. ! 
I've just reinstalled the card (too obvious but too late here in Athens ) and everything is perfect !

Problem solved :)

---

