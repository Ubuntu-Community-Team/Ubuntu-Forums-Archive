---
title: "zombied processes"
date: 2010-01-31
forum: Mythbuntu
---

### Post by linuxhippy on 2010-01-31
I'm running mythbuntu 9.10 and notice that on every boot I get 4-6 zombied processes only when the frontend is running (ssh in or CTRL-ALT-F1 and type top after logged in or ps aux).  I've always thought these are not good...any idea why this happens?

---

### Post by nickrout on 2010-01-31
> **linuxhippy said:**
> I'm running mythbuntu 9.10 and notice that on every boot I get 4-6 zombied processes only when the frontend is running (ssh in or CTRL-ALT-F1 and type top after logged in or ps aux).  I've always thought these are not good...any idea why this happens?

what processes?

they are generally a bad thing. they are caused when a process dies without killing its children.

---

### Post by linuxhippy on 2010-01-31
Here are 4 running now from ps aux:

tux       3008  0.0  0.0      0     0 ?        Z    17:49   0:00 [mythfrontend.re] <defunct>
tux       3010  0.0  0.0      0     0 ?        Z    17:49   0:00 [mythfrontend.re] <defunct>
tux       3012  0.0  0.0      0     0 ?        Z    17:49   0:00 [mythfrontend.re] <defunct>
tux       3014  0.0  0.0      0     0 ?        Z    17:49   0:00 [mythfrontend.re] <defunct>

---

### Post by movieman on 2010-02-01
Looks like your frontend crashed multiple times on startup: you should probably take a look at the log and see if you can find any error messages explaining why the frontend crashed.

---

### Post by linuxhippy on 2010-02-01
> **movieman said:**
> Looks like your frontend crashed multiple times on startup: you should probably take a look at the log and see if you can find any error messages explaining why the frontend crashed.

There's a lot of info in /var/log/messages...would mythtv put errors here?

---

### Post by ffp on 2010-02-01
Hello,

It's a known bug:

[https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/479509](https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/479509)

---

### Post by linuxhippy on 2010-02-01
are there any solutions, yet...like kill -9 xxxx?

---

### Post by movieman on 2010-02-01
> **linuxhippy said:**
> are there any solutions, yet...like kill -9 xxxx?

Zombies are already dead, so you can't kill them. All they should be using is a process ID and a few k of RAM, so they're not a huge problem.

---

### Post by 4dognight on 2010-02-02
Don't you have to shoot them in the head? ;-)

---

