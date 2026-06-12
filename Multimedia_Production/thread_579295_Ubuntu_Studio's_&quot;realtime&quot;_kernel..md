---
title: "Ubuntu Studio's &quot;realtime&quot; kernel."
date: 2007-10-18
forum: Multimedia Production
---

### Post by Sunnz on 2007-10-18
Just wondering what's the difference between   

linux-image-rt and   linux-rt

And where can I get the kernel source and config files that were used to build them?

Thanks.

---

### Post by eye208 on 2007-10-18
"linux-rt" is a meta package. It does not contain any files, but if you install it, you will get both "linux-image-rt" and "linux-restricted-modules-rt" as well. These are meta packages themselves, linking to the most recent versions of the actual kernel and modules packages. Think of it as a dependency tree with linux-rt at its root. Consequently, linux-rt is the package you would want to install if you need the latest realtime kernel.

Edit: Wait, it's not "linux-rt" but "linux-lowlatency", right?

---

### Post by Sunnz on 2007-10-18
>  Edit: Wait, it's not "linux-rt" but "linux-lowlatency", right?

Oh, I don't know, I was thinking about the kernel that Ubunt Studio installs by default. But anyway, thanks for the explanation, it surely clears up confusions! :)

---

### Post by Jussi01 on 2007-10-18
No, its -rt. the -lowlatency kernel is a predecessor to the rt. RT kernel replaces it. :)

---

### Post by eruditelite on 2007-11-06
What about the kernel source for linux-rt?

---

