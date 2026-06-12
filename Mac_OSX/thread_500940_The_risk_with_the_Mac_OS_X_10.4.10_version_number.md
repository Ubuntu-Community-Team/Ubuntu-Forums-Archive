---
title: "The risk with the Mac OS X 10.4.10 version number"
date: 2007-07-14
forum: Mac OSX
---

### Post by BoyOfDestiny on 2007-07-14
Stumbled upon this while reading the Risks Digest:

> 
The initial three [sic] digits for "10.4.10" are the same as "10.4.1," an
earlier release of Mac OS X 10.4 (Tiger). Since the
"MAC_OS_X_VERSION_ACTUAL" string (used by Cocoa applications to determine
the current OS version) can carry a maximum of four digits, Mac OS X 10.4.10
and and 10.4.1 are both labeled "1041."

This means that some applications recognize Mac OS X 10.4.10's version
string as Mac OS X 10.4.1 and refuse to properly run, erroneously thinking
that the system version is too old. For instance, the application UNO
requires Mac OS X 10.4.4. When running under Mac OS X 10.4.10, it recognizes
the Mac OS X version number as 10.4.1 and refuses to operate.


[http://catless.ncl.ac.uk/Risks/24.72.html#subj3](http://catless.ncl.ac.uk/Risks/24.72.html#subj3)

---

### Post by juxtaposed on 2007-07-14
I thought it was weird they did the 10.4.10 thing because 10.4.1 = 10.4.10 with the whole math thing. When I saw they were at 10.4.9 I thought it was the last one till leopard.

---

### Post by Auria on 2007-07-16
> **juxtaposed said:**
> I thought it was weird they did the 10.4.10 thing because 10.4.1 = 10.4.10 with the whole math thing. When I saw they were at 10.4.9 I thought it was the last one till leopard.

that's probably what they meant to do but found new bugs...

---

### Post by max.diems on 2007-07-16
Even worse when it gets to OSX 10.10 (Also, isn't OSX 10.*y* rather redundant?)

---

### Post by 3rdalbum on 2007-07-17
Anyone who builds DRM into their programs to check what SUB-SUB-version of the operating system is being used and deny service to people with an older sub-sub-version, deserves to have to go back into their source code and change their detection code like the fools they are.

I've even seen websites where the developer has ASSUMED that Flash 7 would be the last version of Flash Player ever made, and so people with Flash 9 failed the plugin detection and were denied access to the website. Some programmers should be shot.

---

### Post by metallicamaster3 on 2007-08-02
after 10.4.9 they couldve done 10.4.9.1 but that wouldve totally screwed everything up, and ruin the way they release updates and all...

---

### Post by Alfa989 on 2007-08-02
> **3rdalbum said:**
> Anyone who builds DRM into their programs to check what SUB-SUB-version of the operating system is being used and deny service to people with an older sub-sub-version, deserves to have to go back into their source code and change their detection code like the fools they are.

Gonna say it loud and clear:
[COLOR="Red"][SIZE="4"]WTF???
[/SIZE][/COLOR]

What has DRM got to do with a version detection mechanism that is there to PREVENT problems???

We all know Apple has fd it up a bit now, but is it really that important?
It's more like a big: Oops!

---

