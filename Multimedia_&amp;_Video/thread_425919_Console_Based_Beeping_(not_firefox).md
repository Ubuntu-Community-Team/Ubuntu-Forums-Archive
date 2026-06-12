---
title: "Console Based Beeping (not firefox)"
date: 2007-04-28
forum: Multimedia &amp; Video
---

### Post by drewrockshard on 2007-04-28
I am running Ubuntu 6.06 LTS Server.

There has bee numerous posts about beeping issues regarding Firefox something or other, but not for the issue I am having, so away I go with creating a new post.

When doing a tab completion that may not yield anything, or doing tab completions before it gives me the choice of displaying all info, it beeps.  This is quite annoying and I do not know how to remove this beeping sound.  I know that this "beeping" sound is on the motherboard, and yes, I could turn it off, but I know theres a way to do it in Ubuntu (how I do not know), as I do not want to disable the beeping altogether, as it comes in really handy in case my mdadm array fails or if I have to load a live CD to recover anything, I want to still be notified.

Remember, I am running in a console based environment. Run level 3, I don't even have X installed.  So please let me know what I need to type in the bash prompt.  Thanks in advanced.

- Drew

---

### Post by Jussi Kukkonen on 2007-04-28
Not sure if this is what you want, but... To permanently silence the beeper, add the line
```
blacklist pcspkr

```
in */etc/modprobe.d/blacklist*

---

### Post by drewrockshard on 2007-04-28
Nope, sorry that didn't work.  It is still beeping.  Do I need to restart a certain service? 

Thanks for your reply though, anybody have any other possible ways?

---

### Post by reclusivemonkey on 2007-04-28
Try

```

setterm -blength 0

```

in /etc/profile (system wide) or ~/.bash_profile (per user). This one drove me mad whilst I was using cygwin at work...

---

### Post by drewrockshard on 2007-04-28
> **reclusivemonkey said:**
> Try

```

setterm -blength 0

```

in /etc/profile (system wide) or ~/.bash_profile (per user). This one drove me mad whilst I was using cygwin at work...

Thank you so much, man.  I appreciate this.  Worked like a charm.

Regards,
Drew

---

