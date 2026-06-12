---
title: "very slow X"
date: 2008-08-13
forum: Multimedia Software
---

### Post by Marcin Nawrocki on 2008-08-13
I've got Athlon x2 3800 with Radeon 3850.
After I've installed envy drivers everything seems to work ok, there is 2d and 3d acceleration and so on.
But X works very slow, there is very high usage of the CPU by Xorg task.

---

### Post by estyles on 2008-08-14
I have the same problem, except it just started recently.  Actually, it started a while back when I was running Hardy, and was one of the reasons I decided to start using Linux Mint instead (basically the same thing, with a few addons), because I figured I screwed something up.  Now the problem is back in Mint, and I can't figure out how to get rid of it or what I could have possibly done to cause it.  Here's a workaround that works for me: ```
metacity --replace
```
Using metacity instead of compiz seems to get rid of the lag, but it's not an ideal solution, because I really got used to having compiz on and really like some of its effects and shortcuts.  Worse, my transparent desktop terminal doesn't seem to work right in metacity, and I've grown to rely on it as a crutch.

Anyone know why Xorg would suddenly freak out like this and whether or not it has something to do with compiz (which I haven't modified in weeks)?  A side note, I get the following in my /var/log/messages:```
Aug 14 22:12:15 bacchus kernel: [  159.337911] glxinfo[6782]: segfault at 00000200 eip b7fb5bad esp bfc94040 error 4
Aug 14 22:12:15 bacchus kernel: [  159.380348] glxinfo[6786]: segfault at 00000200 eip b7fa1bad esp bfddfbd0 error 4
Aug 14 22:12:15 bacchus kernel: [  159.430518] glxinfo[6792]: segfault at 00000200 eip b7f43bad esp bf86d660 error 4
Aug 14 22:12:15 bacchus kernel: [  159.539136] glxinfo[6813]: segfault at 00000200 eip b7ff3bad esp bf8c4eb0 error 4

```

Edit: It doesn't seem like compiz is causing it - AFAICT, switching to metacity speeds up the system just because metacity is so much lighter than compiz.  When I move windows around, Xorg's processor usage still jumps up way more than it should, but I don't notice it as much with metacity.  About 95% CPU usage when moving windows with compiz active, and about 65-70% cpu usage when moving a window with metacity active.  I'm sure it has something to do with that glxinfo segfault, but I can't decipher what that error means.

---

