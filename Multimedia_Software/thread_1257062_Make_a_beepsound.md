---
title: "Make a beep/sound"
date: 2009-09-03
forum: Multimedia Software
---

### Post by mmendez on 2009-09-03
All I am trying to do is make a beep in 9.04. I have searched google and here and all I find is how to get rid of the beep. 

Now my comp doesnt have a pc speaker so "^G" or "\a" don't work. So I guess I am left with having to use pulse or also or oss, I don't understand which is the one to use. Ok so all I want is to make a sound through the shell by any means possible.

And I have installed "beep" and it doesn't work with /dev/audio, dev/dsp, /dev/mixer

I have a pair of speakers connected to the motherboard and sound works just fine.

Thanks

---

### Post by DaithiF on 2009-09-07
about the only way i can coax a beep from my system is:
```
echo -e "\a" | sudo tee /dev/tty1

```

---

### Post by mmendez on 2009-09-08
Nope, still nothing.

---

