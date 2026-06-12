---
title: "Dual Monitor/Visual Effects/Compiz Issues/Questions"
date: 2009-02-14
forum: Multimedia Software
---

### Post by josheby on 2009-02-14
I have two 19" LCD Samsung Monitors.  I have an ATI Radeon X800XL with 256MB of memory.

In cloned mode I can run visual effects fine, but when I try to extend the desktop they do not work.

josheby@josheby:~$ compiz
... 
Comparing resolution (2560x1024) to maximum 3D texture size (2048): Failed.
...

I have read on some pages that this can be remedied by getting a new video card?  If so, what spec do i need to make sure the new card has?  From my reading I have found that its because this card has a maximum 3D texture size of 2048x2048.  Can anyone point me to a cheaper video card that will support what I am looking for?

Any advice/suggestions are welcomed.  Thanks!

---

### Post by josheby on 2009-02-15
I looked up the stats on my video card... ATI X800XL...  It lists the maximum resolution as 2048 x 1536 / 85 Hz... is this why I cannot use compiz/visual effects when using my dual monitors?  Because my desktop is actually 2560 pixels wide?

how about this card?

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814133209]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814133209")

In the specs it lists maximum resolution as: 2560 x 1600

Would this card pass the test when I run the compiz command in terminal?

---

### Post by josheby on 2009-02-16
Does anyone know the answer to this?  Any advice would be appreciated...  Thanks!

---

### Post by PiCkAjEw on 2009-03-02
> **josheby said:**
> Does anyone know the answer to this?  Any advice would be appreciated...  Thanks!

I think it's one of those "it's not you, it's me" kind of situations. So it's not the hardware, it's the driver, I think. Here is the bug report and a potential patch:

[https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/146298](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/146298)

---

### Post by Daremo_06 on 2009-03-03
Though I am running different hardware, I am seeing the exact same issue.  I am going to try the solution presented in the bug report at the end and report back here if it works or not.

---

### Post by Daremo_06 on 2009-03-03
How do you install the patch in the above link?  I got to the bottom of the page linked there and there is a patch mentioned... how do I install/compile that?  I'm a fairly new user of Linux so some of this is going right over my head.  

Thanks

---

