---
title: "Issue with graphics - tearing"
date: 2014-10-20
forum: Multimedia Software
---

### Post by damien14 on 2014-10-20
Hi,
I've just finished installing Xubuntu 14.04 on my computer and I noticed slight but annoying kind of blurry stripe across the screen when scrolling fast, or watching videos, which I believe is called tearing.
My graphic card is :
```
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)


```

I've installed the latest 1.0.6. drivers, which didn't changed. I'm a bit puzzled because I've never experienced that with other distros on the same computer (Mint, elementary).
Can anyone help me solve that problem ?
Thanks a lot,
D.

---

### Post by Toz on 2014-10-20
Hello and welcome.

Does it help if you enable the "Synchronize drawing to the vertical blank" option in Settings Manager >> Window Manager Tweaks >> Compositor tab?

---

### Post by damien14 on 2014-10-21
Hi, thanks for your answer !
Unfortunately this did not do the trick, the tearing is still there...

---

### Post by damien14 on 2014-10-21
HI, I've found the solution for this problem using compton thanks to this thread [http://ubuntuforums.org/showthread.php?t=2144468](http://ubuntuforums.org/showthread.php?t=2144468) .
I feel stupid for not finding this before, I just wasn't entering the right search terms.
Cheers,
D.

---

