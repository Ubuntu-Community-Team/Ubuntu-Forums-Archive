---
title: "Real Time Kernel Patches to be integrated in mainstream kernel"
date: 2006-08-24
forum: Multimedia &amp; Video
---

### Post by Peturrr on 2006-08-24
Interesting development.

[http://www.internetnews.com/dev-news/article.php/3627831](http://www.internetnews.com/dev-news/article.php/3627831)


 [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=-1]Real Time operating systems have traditionally been a separate breed from mainstream ones.   [/SIZE][/FONT]
[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=-1]Thanks to efforts to incorporate Real Time enhancements into Linux, standard mainstream Linux may well become a real, Real Time OS real soon. [/SIZE][/FONT]
 [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=-1]A Real Time OS offers the promise of better response times and a degree of determinism not found in non-Real Time OS's. 
[/SIZE][/FONT]
[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=-1]One such Real Time enhancement is something called preemptive scheduling. [/SIZE][/FONT]
 [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=-1]"When a process enters the kernel and a higher priority process needs to execute, I want to stop the process that is running and then let the higher priority run and then return," Dietrich explained. [/SIZE][/FONT]
 [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=-1]He said that there are a number of inhibitors to Real Time in the 2.6.x kernel, not the least of which is the fact that there are some 11,000 critical sections that are not preemptable.[/SIZE][/FONT]
[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=-1]
In the Real Time Linux kernel there are high-resolution timers and preemptable interrupt handlers in thread context according to Dietrich. [/SIZE][/FONT]
 [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=-1]With the Real Time Linux kernel, Dietrich claimed that response time can be reduced by an order of magnitude.[/SIZE][/FONT]

[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=-1]**Over the next year and a half, the Real Time enhancements will be merged into the mainstream Linux kernel, according to Dietrich. High-resolution timers are expected to debut in the 2.6.19 kernel.**

[/SIZE][/FONT][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=-1]**Interrupt threads are expected in the 2.6.20 kernel, and by the time the 2.6.22 kernel rolls around all of the Real Time patches should be integrated**. [/SIZE][/FONT]

---

### Post by dolson on 2006-08-24
Wow. Thanks so much for posting this news. This is very very good news indeed!

---

