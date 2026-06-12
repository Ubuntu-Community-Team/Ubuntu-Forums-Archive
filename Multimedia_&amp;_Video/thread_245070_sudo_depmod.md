---
title: "sudo depmod"
date: 2006-08-27
forum: Multimedia &amp; Video
---

### Post by toasted on 2006-08-27
Hi

I just compiled a kernel and found 2 different sets of instructions

one contained 
```

sudo depmod 
```
and the other
```
sudo depmod -a
```

I read the man but it doesnt say much about -a

Could someone explain please?  

tia

---

### Post by toasted on 2006-08-27
Should I post this in the beginner section instead or is it just that nobody knows the answer?

---

### Post by Culito on 2006-08-27
```
man depmod
```

-appears to be a "quick" option.

---

### Post by toasted on 2006-08-27
Ahhh yes I see it now
```

       -A --quick
                 This  option  scans  to see if any modules are newer the mod&#8208;
                 ules.dep file before any work is done: if  not,  it  silently
                 exits rather than regenerating the files.
```

Thanks for the post, it made me look again  LOL

---

### Post by Culito on 2006-08-28
I like toast.  With butter.

---

