---
title: "Lubuntu 15.10 &quot;Always on top&quot; does not work correctly with Compton!"
date: 2016-03-15
forum: Multimedia Software
---

### Post by Yashalta on 2016-03-15
I configure the compton.conf that if exists INactive window/s it is become a transparent.
Also I have a function "Always on top", this function does not work correctly with Compton! Because _Compton make the window transparent like inactive window, even if the function "Always on top" is ON!_ The function "Always on top" works well without Compton!

I think to me need to make an _exception_ for Compton like [U]"Do not make the window transparent if enabled function "Always on top"!

[/U]I can make an exception on compton for conky like exception always in fokus **"focus-exclude = [ "class_g = 'conky'" ];**"  or exception always opaciti=1  **"opacity-rule = [ 'class_g = "conky":1.00' ]**".
But how to do same exception for functions "Always on top" i dont know!Please, HELP!!!

PS - Lubuntu 15.10 Feature "Always on top" does not work correctly with Compton!

---

### Post by ajgreeny on 2016-03-15
I have edited the thread title to make it clear which OS you are asking about.

I use compton im my Xubuntu 14.04 and "always on top" is working well for that, but it does, of course, use another window manager.
Are there any openbox configuration changes that might have some effect in this?

---

### Post by Yashalta on 2016-03-17
> **ajgreeny said:**
> ...to make it clear which OS you are asking about.

Sorry it is important, agree!
Lubuntu 15.10

I answer to myself!
 MANY THANKS to user [f1u77y]("https://www.linux.org.ru/people/f1u77y/profile") from this forum [https://www.linux.org.ru/forum/general/12437023?lastmod=1458156158983](https://www.linux.org.ru/forum/general/12437023?lastmod=1458156158983)
 If briefly insert this line

[B]opacity-rule = ["99:_NET_WM_STATE@:a *= 'ABOVE'"]
[/B]
in file of compton.conf

---

### Post by ajgreeny on 2016-03-19
Great!

There can be a few cases where specific entries are needed for applications in the compton.conf file; I have to use a shadow exception entry for virtualbox in fullscreen, (which is how I always use it), or the guest fullscreen window is too dark to see anything at all.

Please mark the thread as SOLVED from the Thread Tools menu at the top.

---

