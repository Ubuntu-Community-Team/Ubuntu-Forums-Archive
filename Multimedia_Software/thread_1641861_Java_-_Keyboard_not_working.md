---
title: "Java - Keyboard not working"
date: 2010-12-09
forum: Multimedia Software
---

### Post by rouge568 on 2010-12-09
So I was having an issue with java keyboard input (to be specific, I was trying to play minecraft), and I solved it! Since I couldn't find my solution online, I decided to post it here in case anyone else ever has a similar problem. Ok, so here goes.

**The Problem:**
I was running a java applet, both in browser and standalone. My mouse worked perfectly fine, clicking and moving around well, but all keyboard input was broken. Trying to type anything in the java window just didn't work. In other programs, it still worked well.

**The Explanation:**
For some reason, SCIM does not play nice with java. I had completely forgotten that I was running SCIM in the background (I occasionally switch over to chinese characters), and so it did not occur to me that it could be causing problems. If anyone knows why this is (or has a more elegant fix), please post below.

**The Solution:**
You just need to disable SCIM! Going into the system monitor and killing all the SCIM processes fixed the problem for me, and the keyboard worked perfectly on java. Alternatively, you could run ```
killall -v scim scim-launcher scim-panel-gtk
```

That's all folks!

---

