---
title: "mac osx and bash"
date: 2008-08-31
forum: Mac OSX
---

### Post by sulekha on 2008-08-31
Hi ,

 I have read in the book "Ubuntu Linux Tool Box" by Christopher Negus
 and Francois caen that: bash is the shell used by default by most modern linux systems and quite few other operating systems such as Mac OSX.

 1 To what extent these statements are true especially regarding Mac OSX
 2 why Mac OSX is providing a bash shell, is it something similar to cygwin ?

---

### Post by aloshbennett on 2008-08-31
Mac OS X is based on unix, and not just a unix-like-environment like cygwin. By default, OS X ships with bash as its terminal shell.

Tip: you can always find your shell by trying
> ps $$

---

### Post by Rocket2DMn on 2008-08-31
Moved to the Mac OSX forum area.
For the record, OSX is based off of BSD which is based off of UNIX.

---

### Post by Bachstelze on 2008-08-31
1. It is true to some extend. AFAIK, Mac OS X is the only non-GNU OS that uses Bash as its default shell.

2. No, it is not a hack like Cygwin. Unlike Windows, Mac OS X is a true UNIX-like OS, so I guess Bash was just compiled for it the same way it is compiled on Linux.

---

### Post by EnGorDiaz on 2008-09-02
its wierd how these posts are kind of negligent 

negligent meaning neglectful that a common ubuntu or unix user would try and compare it to cygwin

no offence

---

### Post by 3rdalbum on 2008-09-03
> **HymnToLife said:**
> Unlike Windows, Mac OS X is a true UNIX-like OS

Just thought I'd clarify for the other people here - Mac OS X is Unix-LIKE. As in, it's like Unix, but it's not Unix.

Main difference: Unix respects the Unix security system. Mac OS X doesn't.

---

### Post by saulgoode on 2008-09-03
> **3rdalbum said:**
> Just thought I'd clarify for the other people here - Mac OS X is Unix-LIKE. As in, it's like Unix, but it's not Unix.

Actually, [OS X is Unix](http://www.opengroup.org/openbrand/register/xy.htm).

---

### Post by Bachstelze on 2008-09-04
> **saulgoode said:**
> Actually, [OS X is Unix](http://www.opengroup.org/openbrand/register/xy.htm).

Only 10.5. Previous versions are not, and no precise version number was given here.

---

### Post by 3rdalbum on 2008-09-05
> **saulgoode said:**
> Actually, [OS X is Unix](http://www.opengroup.org/openbrand/register/xy.htm).

Unix is more than an operating system, it's a concept of system design. Just like how Internet Security is more than a Symantec product, it's a process.

OS X might have some Unix underneath, deep down and buried, but the design of the whole operating system is more like what Microsoft would release eight years ago - a hack balanced on a hack balanced on a hack. No real Unix vendor or developer would leave an easy local root vulnerability in the default install of their software for four years after being informed of it.

I guess, if you were less stringent than I, you could describe OS X as "Unix, but not a very good one". :-)

---

### Post by Demio on 2008-09-05
> **3rdalbum said:**
> Unix is more than an operating system, it's a concept of system design. Just like how Internet Security is more than a Symantec product, it's a process.

OS X might have some Unix underneath, deep down and buried, but the design of the whole operating system is more like what Microsoft would release eight years ago - a hack balanced on a hack balanced on a hack. No real Unix vendor or developer would leave an easy local root vulnerability in the default install of their software for four years after being informed of it.

I guess, if you were less stringent than I, you could describe OS X as "Unix, but not a very good one". :-)

Care to elaborate on the "easy local root vulnerability"? 

And what are your arguments for sustaining your opinion about OS X being "a hack balanced on a hack balanced on a hack."

Your post intrigues me. :popcorn:

---

