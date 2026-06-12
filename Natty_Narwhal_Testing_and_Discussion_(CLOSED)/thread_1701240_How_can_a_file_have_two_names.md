---
title: "How can a file have two names?"
date: 2011-03-06
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by JRV on 2011-03-06
Yesterday I created a thread called "How do I add my script to the Unity launcher bar?".
With help form forum members my questions were answered and the problem was solved.

I needed to create a .desktop file.  I copied one of the files from /usr/share/applications to my desktop.  Then I edited it to call my script, renamed it, and moved it to a directory I created called ~/.local/share/applications.

When I look at the file through the GUI I see the name I gave it.
When I look at it in the terminal I see the original name.
When I look at the files in /usr/share/applications through the GUI I see a name, and when I look at them in the terminal I see the same name but with .desktop appended to it.

How can a file have two names?

---

### Post by ronacc on 2011-03-06
if the .desktop extension is the only difference that extension is hidden when using the gui . look at /home/<you>/Desktop with filemanaager and then in the term and you'll wee what I mean .

---

### Post by JRV on 2011-03-06
The files in /usr/share/applications have the same name with the .desktop extension.

The file I created has the original name from before I copied and modified it when viewed in the terminal. That name is "gnomine.desktop".  When viewed through the GUI it is "TC", the name I gave it.

When I try to rename it from the command line it won't let me.
Here is the error message:
```

jack@langsdown2:~/.local/share/applications$ rename gnomine.desktop tc.desktop
Bareword "gnomine" not allowed while "strict subs" in use at (eval 1) line 1.
Bareword "desktop" not allowed while "strict subs" in use at (eval 1) line 1.

```

---

### Post by LemursDontExist on 2011-03-06
You're on the right track!  The 'rename' program, it turns out, uses regular expressions for renaming - and is interpreting your arguments all wrong.  I would just use 'mv'.

```
mv gnomine.desktop tc.desktop
```

I'd actually never seen the rename program before today - it seems useful, but it is designed primarily for batch renaming.  I think correct use of it would be something like:

```
rename 's/gnomine\.desktop/tc\.desktop/' gnomemine.desktop
```

A little baroque for a simple file rename!

---

### Post by JRV on 2011-03-06
Solved

Many thanks LemursDontExist

Everything seemed to work with the different names, but I was afraid it might cause problems later on.

---

