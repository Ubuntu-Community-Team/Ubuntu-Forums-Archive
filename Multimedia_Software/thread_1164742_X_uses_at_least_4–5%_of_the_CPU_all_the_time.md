---
title: "X uses at least 4–5% of the CPU *all* the time"
date: 2009-05-19
forum: Multimedia Software
---

### Post by kumoshk on 2009-05-19
Is this normal? It was a lot worse before I installed my nvidia drivers on my laptop, but it seems like in previous installations my CPU wasn't constantly going (but I could be misleading myself). Now, X takes up at least 4% of the processing power (usually more) all the time.

This doesn't seem like it can be good for the computer.

I think I'll check on my desktop now and see how much of the processor is being taken there.

Anyway, let me know your thoughts and/or knowledge. Thanks!

---

### Post by kumoshk on 2009-05-19
Huh. Looks like it does the same thing on my other computer. Must be normal. Are there any ways to lessen it, though?

---

### Post by psyke83 on 2009-05-20
> **kumoshk said:**
> Huh. Looks like it does the same thing on my other computer. Must be normal. Are there any ways to lessen it, though?

Which application are you using to measure CPU usage? I hope it's merely top, as the GNOME System Monitor saps a lot of CPU drawing the CPU usage graphs, etc.

---

### Post by kumoshk on 2009-05-20
> **psyke83 said:**
> Which application are you using to measure CPU usage? I hope it's merely top, as the GNOME System Monitor saps a lot of CPU drawing the CPU usage graphs, etc.

I'm using xfce4-taskmanager (although I'm using Gnome&#8212;not Xfce; I just like Xfce's graphical task manager). Thanks for the note on top&#8212;I had forgotten what the name of that program was.

---

### Post by mcduck on 2009-05-20
> **kumoshk said:**
> Is this normal? It was a lot worse before I installed my nvidia drivers on my laptop, but it seems like in previous installations my CPU wasn't constantly going (but I could be misleading myself). Now, X takes up at least 4% of the processing power (usually more) all the time.

This doesn't seem like it can be good for the computer.

I think I'll check on my desktop now and see how much of the processor is being taken there.

Anyway, let me know your thoughts and/or knowledge. Thanks!
That's absolutely normal, and in no way harmful to your computer. After all, the hardware should be able to run at continuous 100% use for it's full lifetime. Using couple of percents of what the hardware is capable of doing is definitely not going to break anything.. :D

Also you should know that every graphical app you have running will also add a bit to X's resource usage, so if you see X using a lot of resources it's most of the time actually caused by some other program you have open, not X itself.

---

