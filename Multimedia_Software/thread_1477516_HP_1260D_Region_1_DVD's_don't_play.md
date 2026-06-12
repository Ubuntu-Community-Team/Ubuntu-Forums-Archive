---
title: "HP 1260D: Region 1 DVD's don't play"
date: 2010-05-08
forum: Multimedia Software
---

### Post by jonnan on 2010-05-08
I have two HP DVD Burners attached to my new Ubuntu DVR system. An older external HP 680 burner reads them fine, so at this point I'm assuming it's a region issue, but setting regionset to region 1 has made no difference.

It *does* read older DVD's I've recorded (Which I'm assuming are region 0) without issue, which is not entirely un-useful - I have a lot of them. But the new one doesn't seem to read any DVD I've bought.

I'd like to thank the film industry for helping me save money through their unfair trade practices btw. I'm sure they didn't want my money anyway - <G>.

Thanks - Jonnan
regionset output
> $ sudo regionset
regionset version 0.1 — reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: NONE
vendor resets available: 4
user controlled changes resets available: 5
drive plays discs from region(s):, mask=0xFF

Would you like to change the region setting of your drive? [y/n]:y
Enter the new region number for your drive [1..8]:1
New mask: 0xFFFFFFFE, correct? [y/n]:y
Region code set successfully!

> $ sudo regionset
regionset version 0.1 — reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: SET
vendor resets available: 4
user controlled changes resets available: 4
drive plays discs from region(s): 1, mask=0xFE

---

