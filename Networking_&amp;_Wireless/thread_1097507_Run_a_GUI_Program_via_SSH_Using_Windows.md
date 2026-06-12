---
title: "Run a GUI Program via SSH Using Windows"
date: 2009-03-16
forum: Networking &amp; Wireless
---

### Post by Fireblazer on 2009-03-16
Hey,

I just installed SSH on my Ubuntu computer and I'd like to be able to run a GUI program using PuTTY (or other windows SSH client). I've read about how to do it on linux but nothing for Windows, can anyone help me?

~ Fireblazer

---

### Post by vlovich on 2009-03-16
I'm confused about what exactly you're trying to do.  Are you saying you want to run your GUI Linux programs on Windows?

If so, you'll need to install an X server on Windows (i.e. Xming) & run putty with X forwarding option enabled.

Is that what you're trying to do?

---

### Post by buldozerceto on 2009-03-16
I think you can run the program but first you need to run the x server on the ssh bo, and with a proper command the gui on the ssh box may start. Though I think you won't see anything on your remote box.

---

### Post by Fireblazer on 2009-03-16
Yup Vlovich, that's exactly what I'm trying to do.
I'll try that, thanks

~ Fireblazer

---

