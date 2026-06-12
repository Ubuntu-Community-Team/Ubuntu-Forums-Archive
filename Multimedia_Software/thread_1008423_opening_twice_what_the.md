---
title: "opening twice? what the"
date: 2008-12-11
forum: Multimedia Software
---

### Post by dcperkins on 2008-12-11
So today is my day that i try to fix all my issues with the rhythm box that i have been ignoring for a year, so bear with me. 

So when i open, or rather attempt to open rhythm box i have to do it twice.  its really strange, i go to applications>sound and video>rhythm box and click and my mouse spins its wheeles a box pops up on the bottom saying "starting rhythm box" and then they both stop and nothing happens, and theni have to do it again and it opens. 
clues?

---

### Post by cariboo on 2008-12-11
Open Rhythmbox in a Applications-->Accessories-->Terminal and note if there are any error messages, and paste them into your next post.

Jim

---

### Post by dcperkins on 2008-12-11
i dont actually know how to do that. I mean, i can get to my terminal, but then i dont know what to do to open rb.
sorry, and thanks.

---

### Post by kostkon on 2008-12-11
> **dcperkins said:**
> i dont actually know how to do that. I mean, i can get to my terminal, but then i dont know what to do to open rb.
sorry, and thanks.
just give
```
rhythmbox
```
or in debug mode
```
rhythmbox -d
```
but it will create a hell of an output, so you could pipe it to a text file like this
```
rhythmbox -d > ~/rhythmbox_out.txt
```

---

### Post by dcperkins on 2008-12-11
sweet.
this is what it said
(14:33:17) [0x9101408] [rb_debug_init_match] rb-debug.c:215: Debugging enabled
(14:33:17) [0x9101408] [main] main.c:187: initializing Rhythmbox 0.11.6
(14:33:17) [0x9101408] [rb_threads_init] rb-util.c:389: GMutex isn't recursive
(14:33:17) [0x9101408] [main] main.c:195: going to create DBus object
(14:33:17) [0x9101408] [main] main.c:347: THE END

ok now what?

---

### Post by fotherington on 2009-02-01
I'm getting exactly the same commandline result as dcperkins - fully updated Intrepid and all. Where does Rhythmbox log its errors?

---

