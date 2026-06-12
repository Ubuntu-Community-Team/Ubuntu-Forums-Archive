---
title: "mp3 real time recording"
date: 2007-11-02
forum: Multimedia &amp; Video
---

### Post by tanozfood on 2007-11-02
Hello,
I use this pipe to record analog line input into mp3:

arecord -f cd | lame -q 2 out.mp3

However, during last recording the pipe was broken after about 3 hours
of recording. I think about some problem with the infamous 2 GB limit
of the standard C library. Looking with strace to arecord and lame
I see that open() system calls have the O_LARGEFILE enabled, so?
How can I make things work?
Or which another tool? (because my pc is old - celeron 600 MHz, top
shows that I use the 60 % cpu time to lame, I prefer a command line tool)
Thanks,
                     Gaetano

---

