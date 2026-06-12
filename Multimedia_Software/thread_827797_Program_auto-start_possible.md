---
title: "Program auto-start possible?"
date: 2008-06-13
forum: Multimedia Software
---

### Post by jackirby on 2008-06-13
First Post... Hope I don't seem too stupid!
I'm trying to record TV from my composite input on my tuner card as I have foxtel hooked up to it. I've managed to do it by making a shortcut in my panel which uses mencoder with a bucketload of options to record the input, but I want to know if I can get a program to start the recording automatically. In other words, is there a way to have programs startup at an arbitrary time rather than only at startup? and if so, is there a way to stop them after a pre-determined time?

Thanks for any help! I've been trudging through google, but so far only getting startup stuff :(

---

### Post by renzokuken on 2008-06-13
maybe a cron job could do it... you could make a simple bash script to execute the commands and set a cron job up to execute your script at a given time

[http://www.unixgeeks.org/security/newbie/unix/cron-1.html](http://www.unixgeeks.org/security/newbie/unix/cron-1.html)

---

### Post by easybake on 2008-06-13
You could try to use the ideas in this page to try and do something similiar.[http://joeamined.wordpress.com/2008/02/15/automatically-changing-wallpaper-relatively-to-daytime-in-ubuntu/]("http://joeamined.wordpress.com/2008/02/15/automatically-changing-wallpaper-relatively-to-daytime-in-ubuntu/")Obviously you would edit the script to fit your needs. I have no clue what the stop command would be. It's worth taking a look.

Note: Remove the quotes around HOUR. Also the cron should be ```
* 4,8,16,19 * * *sh YOUR-HOME-FOLDER/.change.sh
``` not what they have posted

---

### Post by jackirby on 2008-06-15
Thanks guys... Much appreciated :)

With no stop command there's not much point though... will just have to start and stop recording manually, which is probably better as I won't have useless bits at either end...

Cron is a very cool program! I think I'll be using it in some form... like an alarm clock to get me out of bed with amarok perhaps!

Keep up the great work, without guys like you I think ubuntu would be too big a leap for the average user to let go of windows once and for all.

---

