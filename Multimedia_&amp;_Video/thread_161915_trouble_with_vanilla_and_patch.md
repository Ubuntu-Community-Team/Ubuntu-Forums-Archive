---
title: "trouble with vanilla and patch"
date: 2006-04-18
forum: Multimedia &amp; Video
---

### Post by zorlab on 2006-04-18
I know it is a bit premature to begin re-compiling the kernel (right term?)have only newly experienced Ubantu.. and only having minor experience with terminal commands.
I tend to dive in...

here is what I have begun to do:
[COLOR="Teal"]**apply a patch to the the official vanilla kernel sources. (which install) This patch gives you roughly 95% preemption, as compared to about 50% preemption without the patch**.[/COLOR]

Ref: [http://ubuntustudio.com/wiki/index.p...ime_Preemption](http://ubuntustudio.com/wiki/index.p...ime_Preemption)

I got all the way through install kernel-packages with 2 errors.

```
In file included from drivers/net/skge.c:43:
drivers/net/skge.h:2477: error: duplicate member ‘hw_lock’
make[3]: *** [drivers/net/skge.o] Error 1
make[2]: *** [drivers/net] Error 2
make[1]: *** [drivers] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.15.6-rt21'
make: *** [stamp-build] Error 2
```


In the walk through the next step was
"Once that is complete with no errors, you can then install the new deb packages"


Ignoring the errors I tried the next step but cannot go further, the file [COLOR="Teal"]***2.6.15.6-rt*.deb**[/COLOR]
is not there.

Is there something to do? something I missed? or should I crawl back to baby steps and leave this to another time?

---

### Post by dolson on 2006-04-18
You have the same issue as this earlier thread: [http://ubuntuforums.org/showthread.php?t=158747](http://ubuntuforums.org/showthread.php?t=158747)

The problem is the patch. I don't know why Ingo's patch is not applying fully for some people.

Just a _guess_ from the error message: Edit the file drivers/net/skge.h at line 2477 or so, and you'll see the same line listed twice, regarding hw_lock. Delete one instance of that line, and carry on.

---

### Post by daveZ on 2006-04-22
Yeah. I had the *exact* same problem that zorlab described. I followed dolson's advice, deleting the second instance of the line (toward the bottom of the file drivers/net/skge.h) that mentions hw_lock.

Here is what I saw:

```

	struct tasklet_struct ext_tasklet;
	spinlock_t	     hw_lock;
	spinlock_t	     phy_lock;
	spinlock_t	     hw_lock;
};

```

And here is what I changed it to:
```

	struct tasklet_struct ext_tasklet;
	spinlock_t	     hw_lock;
	spinlock_t	     phy_lock;
};
```

After I did that it compiled just fine.

Thank you dolson!

~daveZ

---

### Post by jmxhgyZN8wK7 on 2006-04-25
WOOOHOOOO!

for the moment, you have restored my faith in linux!

i'm gonna try that when i get time.

---

### Post by dolson on 2006-04-27
Heh, don't let an issue compiling a completely unsupported kernel patch get you down on Linux. :)

---

