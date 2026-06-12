---
title: "upgraded to 10.4, mythfilldatabase not running automagically"
date: 2010-05-30
forum: Mythbuntu
---

### Post by tedder on 2010-05-30
So I upgraded from 8.whatever to 10.4. I've gotten past most of the hiccups, but mythfilldatabase isn't running automagically. I'm running it by hand now, no problem with that. It's been a few years, but I seem to recall there is a checkbox *somewhere* to enable it. Where's that at?

In other words, this is an easy problem, how do I make mythfilldatabase run daily, preferably at a time of my choosing?

---

### Post by ian dobson on 2010-05-30
Hi,

There are options in mythsetup under video source to configure your grabber and the times that it should run.

EDIT: Maybe setup mythfilldatabase to log to a file, it could well be that the grabber is starting but not grabbing any data. You can also try running mythfilldatabase from the terminal prompt, just make sure you start it as the mythtv user with something like:-
su mythtv
mythfilldatabase  --max-days 8  --refresh-all 

Regards
Ian Dobson

---

### Post by klc5555 on 2010-05-30
You can also very simply set the mythfilldatabase job up as a cron job. Since the "daily" crontab that is already in Ubuntu never executes when you would really like it to (and since mythfilldatabase does not require root privileges), you can set the precise minute daily that your mythfilldatabase job would run by setting up a new crontab under your own user account with "crontab  -e"

Read the short manual page on crontab for formatting details: "man crontab". Your crontab for mythfilldatabase will be a one-line file.

---

### Post by tedder on 2010-05-30
> **klc5555 said:**
> You can also very simply set the mythfilldatabase job up as a cron job. ...Read the short manual page on crontab for formatting details: "man crontab". Your crontab for mythfilldatabase will be a one-line file.


Yeah, I definitely don't need the man for crontab (and it's "man 5 crontab" to get the user-facing cron). But I wanted to know the *right* way to do it, which is what Ian gave.

---

### Post by klc5555 on 2010-05-30
> **tedder said:**
> Yeah, I definitely don't need the man for crontab (and it's "man 5 crontab" to get the user-facing cron). But I wanted to know the *right* way to do it, which is what Ian gave.

Whatever floats your boat. There's always more than one solution to Linux problems. Any one that works ad hoc is by definition "right".

Cheers!

---

### Post by tedder on 2010-05-30
> **klc5555 said:**
> Whatever floats your boat. There's always more than one solution to Linux problems. Any one that works ad hoc is by definition "right".

Cheers!

Very true. And I'm guessing you are a perl programmer, not a python programmer by that statement :-)

---

