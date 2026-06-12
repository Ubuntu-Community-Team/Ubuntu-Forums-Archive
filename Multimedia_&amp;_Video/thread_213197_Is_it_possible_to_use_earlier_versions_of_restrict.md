---
title: "Is it possible to use earlier versions of restricted modules with current kernel?"
date: 2006-07-11
forum: Multimedia &amp; Video
---

### Post by handy on 2006-07-11
**_Edit: Please ignore?_**

I have a problem trying to run Guild Wars via Cedega.

I could do it on Breezy, but not on Dapper.  So, I kept my Breezy drive specifically for GW.

I had to reinstall Breezy a few days ago, & guess what, I have the same problem that I have when trying to run GW on Dapper!!!

The problem is that GW doesn't recognise my graphics card (6800GT) which it used to do beautifully.

When I installed Breezy I used Automatix to add some softwares, including the latest nVidia restricted drivers.

Yes, we are finally getting to my question...

I am wondering if the reason that I can't play GW is due to a later nVidia driver version causing the problem?

Can I use an earlier driver?  The possible complexities of this problem are beyond my current knowledge.

Any input greatly appreciated!

---

### Post by handy on 2006-07-11
I have solved the problem another way, so don't anyone take this toughy up please?

---

### Post by tseliot on 2006-07-11
> Is it possible to use earlier versions of restricted modules with current kernel?
No, it's not. The restricted modules are modules compiled for your kernel.

Check that your direct rendering is enabled:
```
glxinfo | grep direct
```

If it's enabled I wouldn't know how to help you (I don't use Cedega).

---

### Post by tseliot on 2006-07-11
> **handy said:**
> I have solved the problem another way, so don't anyone take this toughy up please?

Can you share your solution (other users may benefit from this)

---

### Post by handy on 2006-07-12
> **tseliot said:**
> Can you share your solution (other users may benefit from this)

Thanks for your reply(s) tseliot.  I didn't think it was possible.

I have posted the solution elsewhere, which boils down to this:

Getting Cedega to work (with Guild Wars at least), **can** require, doing the same things over & over, untill it finaly works, then it works reliably from then on!

Pretty technical huh!? :rolleyes: 

I liken it to how it **can** be, setting up a LAN with windoze machines... ](*,)  You keep banging away at it to see who gives in first - your head or the problem! ;) Interestingly enough, the problem is never identified, it just magicaly disapears! :confused: 

Anyone interested in the gory details should [look for post #94 on this page]("http://ubuntuforums.org/showthread.php?t=123715&page=10").

---

### Post by tseliot on 2006-07-12
> **handy said:**
> I liken it to how it **can** be, setting up a LAN with windoze machines... ](*,)  You keep banging away at it to see who gives in first - your head or the problem! ;) Interestingly enough, the problem is never identified, it just magicaly disapears! :confused:
I know what you mean ;)

---

