---
title: "samba logging"
date: 2009-01-09
forum: Networking &amp; Wireless
---

### Post by learner_ubunt on 2009-01-09
hello,
         I am sorry if this is not the right place to post but i badly need your help


        i have my own log levels and a central logging system..         DEBUG() has a newline character after the log message. Problem is i am getting extra newline as my central logger also adds one newline after each log message. I plan to modify the DEBUG macro to strip newline if present. Is it a good idea? How do i go about modifying it?

DEBUG( 0, ( "This is a %s message.\n", "debug" ) );

Thanks in advance for your help!

---

