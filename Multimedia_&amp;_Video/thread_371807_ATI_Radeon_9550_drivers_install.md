---
title: "ATI Radeon 9550 drivers install"
date: 2007-02-27
forum: Multimedia &amp; Video
---

### Post by gmanr26 on 2007-02-27
I've been trying for the last 2 days to install the ATI drivers for Ubuntu, but so far been unsuccesful...

I tried the Ubuntu Wiki attempt, that didn't work...
I tried [this]("http://trueboar.wordpress.com/2007/01/13/ubuntu-edgy-and-ati-step-by-step/#comment-109") tutorial, and as you can see by the comments i've made (I'm Andrew), it hasn't seemed to work....
can someone please help me....
I don't know how to get it working

---

### Post by divague on 2007-02-27
i've used this how to, and it worked

[http://ubuntuforums.org/showthread.php?t=321766&highlight=ati+200m](http://ubuntuforums.org/showthread.php?t=321766&highlight=ati+200m)

---

### Post by gmanr26 on 2007-02-27
ok... so i followed the steps...
and rebooted my machine...
still the window is jerky when i move it around which means to me that the drivers still are not working....

however...
when i go into the terminal and type

fglrxinfo

it gives me

```

> display: :0.0  screen: 0
> OpenGL vendor string: ATI Technologies Inc.
> OpenGL renderer string: RADEON 9550 Generic
> OpenGL version string: 2.0.6234 (8.32.5)

```

please help

---

### Post by doobydave on 2007-02-27
Hi. could you check here :-
[http://www.ubuntuforums.org/showthread.php?t=255929&page=82](http://www.ubuntuforums.org/showthread.php?t=255929&page=82)

to see if you have any other similar logs to me?

---

### Post by gmanr26 on 2007-02-28
i get similar printouts,
how do i fix it?
I'm trying to use the
ati-driver-installer version 8.32.5

---

### Post by doobydave on 2007-03-03
The short answer is..... I dunno.

Maybe try Dapper to see if it behaves any better (or Feisty)

I have filled a bug at launchpad for the problem.
[https://launchpad.net/ubuntu/+source/xorg/+bug/89024](https://launchpad.net/ubuntu/+source/xorg/+bug/89024)

---

