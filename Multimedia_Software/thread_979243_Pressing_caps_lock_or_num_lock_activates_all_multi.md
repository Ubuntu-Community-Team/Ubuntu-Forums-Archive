---
title: "Pressing caps lock or num lock activates all multimedia keys"
date: 2008-11-11
forum: Multimedia Software
---

### Post by jithin1987 on 2008-11-11
I use kubuntu intrepid with kde 4.1.3 on my laptop compaq 6910p. When I press caps lock or num lock all other multimedia keys like volume up and down mute gets activated. Often resulting in muting the sound. This looks so strange that all the button lights blink continuously for a few seconds and assumes some random values audio mostly mutes.

---

### Post by frogotronic on 2009-07-25
> **jithin1987 said:**
> I use kubuntu intrepid with kde 4.1.3 on my laptop compaq 6910p. When I press caps lock or num lock all other multimedia keys like volume up and down mute gets activated. Often resulting in muting the sound. This looks so strange that all the button lights blink continuously for a few seconds and assumes some random values audio mostly mutes.

Same here with Ubuntu on Intrepid Ibex; did you ever find a solution?

- CH

---

### Post by jithin1987 on 2009-07-25
I no loger user Intrepid. It will be better if you upgrade to jaunty.

---

### Post by frogotronic on 2009-07-25
can't just yet - have an R515 series ATI card, open source stack isn't quite there.

But your answer/comment suggests a kernel issue that was resolved in Jaunty.

- CH

---

### Post by jithin1987 on 2009-07-26
If that might be the case you can try getting a newer kernel from here

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by frogotronic on 2009-07-26
> **jithin1987 said:**
> If that might be the case you can try getting a newer kernel from here

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Interesting,  How "new" can I go without breaking my system?  If I install a newer kernel...what about the restricted modules? and other dependencies?

Is there a guide for this?

Thanks,
CH

---

### Post by jithin1987 on 2009-07-26
Well ypu can give it a try and see if the kernel modules compile properly. 

So install dkms package which will take care of compiling your modules.

Any way its not going to break anything in your system. If it does not work you can just boot into your old kernel and remove these packages.

---

