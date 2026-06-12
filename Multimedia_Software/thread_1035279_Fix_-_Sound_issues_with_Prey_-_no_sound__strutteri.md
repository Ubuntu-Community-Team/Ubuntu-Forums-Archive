---
title: "Fix - Sound issues with Prey - no sound / struttering"
date: 2009-01-09
forum: Multimedia Software
---

### Post by interzoneuk on 2009-01-09
Hi.

Just tried the prey-demo - originally the sound was awful.

Here is how i fixed it.

cd to prey directory

mv libSDL-1.2.so.0 libSDL-1.2.so.0.backup

ln -s /usr/lib/libSDL-1.2.so.0 .

Now start prey.

This has worked for me on the following systems - Ubunu x86 + amd64 / opensuse 11.1 amd64

---

### Post by Rytron on 2012-02-23
I could only get sound to work by using Wine 1.1.26 (for full game but probably also works for demo).

---

