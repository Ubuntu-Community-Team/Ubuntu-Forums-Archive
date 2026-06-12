---
title: "new user lost in 11.4"
date: 2011-04-16
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by kooslf on 2011-04-16
I am just trying to get started with Linux.  I barely got started with 10.10 and decided I might as well start learning 11.4.  I am set up to dual boot.  After installing 11.4, I have no display.  I have a 1024MB GeForce 9500 GT (EVGA) graphics card with two monitors.  I am dual booting with windows XP on a dual core pentium 2G memory. I am new to forums, and e-mail is my most modern form of communication.

---

### Post by nothingspecial on 2011-04-16
Well if your learning you're best not using a beta version.........

....... but since you are......

maybe you need a restricted driver

Get a wired connection, after you boot press Ctrl-F1 to get to a console and type

```
jockey-text
```

and see if there are any.

---

### Post by sandyd on 2011-04-16
> **kooslf said:**
> I am just trying to get started with Linux.  I barely got started with 10.10 and decided I might as well start learning 11.4.  I am set up to dual boot.  After installing 11.4, I have no display.  I have a 1024MB GeForce 9500 GT (EVGA) graphics card with two monitors.  I am dual booting with windows XP on a dual core pentium 2G memory. I am new to forums, and e-mail is my most modern form of communication.

try nomodeset.

When booting, press ESC to show grub menu.

press 'e'

using the arrow keys, navigate to the line that starts with "linux".
using the arrow keys, scroll to the end of the line, add a space, and type 'nomodeset' (without quotes)
Then press control +X

---

