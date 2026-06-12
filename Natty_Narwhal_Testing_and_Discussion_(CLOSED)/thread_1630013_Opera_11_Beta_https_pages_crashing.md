---
title: "Opera 11 Beta: https pages crashing"
date: 2010-11-24
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2010-11-24
Is anyone else seeing https sites crashing quite often in Opera 11 Beta (build 1111, 32-bit)? :|

---

### Post by Colonel Kilkenny on 2010-11-24
Nope. But I'm using Maverick. Are other browsers crashing?
Although AFAIK Opera does does not depend on shared libraries when it comes to OpenSSL etc.

edit. Are you using extensions or something which might cause problems (still in early stages of development)?

---

### Post by MacUntu on 2010-11-24
Nope, not seeing it in Chromium and FF.

---

### Post by ronacc on 2010-11-24
give me a reference to a page thats crashing you and I'll try it , I'm on Opera 11b build 1111 64bit

---

### Post by Colonel Kilkenny on 2010-11-25
You could try to start Opera from console to see if it says something when it crashes.

And perhaps you should try to disable JIT to see if it's causing the problems: opera:config#Extensions|EcmaScriptJIT
Although it's a bit difficult to see why it would cause crashes only on https sites...

---

### Post by MacUntu on 2010-11-26
Happening with all HTTPS pages, eg. Launchpad, GNOME Bugzilla, home banking, etc (just not always!). Checking the Opera's Team 
blog comments, it looks like I'm alone with this. Will test it on a second machine now.

> **Colonel Kilkenny said:**
> You could try to start Opera from console to see if it says something when it crashes.
Nothing, the tabs just silently die.

---

### Post by ronacc on 2010-11-26
I havent seen that here , note I do not have Opera 11 installed from .deb . I unzipped the tarball and am starting it from term so that it don't mess with my stable opera install since Opera is my default browser .

---

### Post by Colonel Kilkenny on 2010-12-03
Update, perhaps this helps:
[http://twitter.com/#!/webtoman/status/10706765834358784](http://twitter.com/#!/webtoman/status/10706765834358784)

---

### Post by MacUntu on 2010-12-03
> **Colonel Kilkenny said:**
> Update, perhaps this helps:
[http://twitter.com/#!/webtoman/status/10706765834358784](http://twitter.com/#!/webtoman/status/10706765834358784)

w00t, thanks!

That would also explain why I don't get this on a fresh(er) system.

---

### Post by ronacc on 2010-12-03
also explains wht I did not see it running Opera-11 from the unzipped.tar.gz in its own dir instead of installed , it did not inherit any old stuff from my 10.61 install .

---

### Post by MacUntu on 2010-12-03
> **ronacc said:**
> 10.61

I guess my .opera dir is from the opera 8 era. :D

---

### Post by ronacc on 2010-12-03
I always run the betas from a separate dir and just copy and paste my bookmarks and wand over , I wait until it goes release before I upgrade my main install .

---

### Post by kyleabaker on 2010-12-03
> **MacUntu said:**
> I guess my .opera dir is from the opera 8 era. :D

I haven't been noticing this. I used to just update over an old school Opera setup, but now that Opera Link restores nearly everything I just do a fresh install for most new snapshots. Fewer issues that way. :D

---

