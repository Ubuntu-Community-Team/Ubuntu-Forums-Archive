---
title: "Recording with me-tv"
date: 2009-05-18
forum: Multimedia Software
---

### Post by feuervogel on 2009-05-18
Hello,

I've tried to record a movie with me-tv several times but me-tv does not record the whole movie, it's alsways just a part of it. tried it with different movies:

1st: about 2 hours - recorded 30 minutes less
2nd: 90 minutes - recorded 32 minutes
3nd: test with 6 minutes: recorded only 1:32 minutes

has anyone made the same experience? 

I've been using the ubuntu sources as the developer sources - same problem.

---

### Post by SteveDee on 2009-05-18
> **feuervogel said:**
> Hello,

I've tried to record a movie with me-tv several times but me-tv does not record the whole movie, it's alsways just a part of it. tried it with different movies:

1st: about 2 hours - recorded 30 minutes less
2nd: 90 minutes - recorded 32 minutes
3nd: test with 6 minutes: recorded only 1:32 minutes

has anyone made the same experience? 

I've been using the ubuntu sources as the developer sources - same problem.

I've never had this problem.

I assume you are clicking on a program in the EPG to record. Does the dialog box then show the correct start time and duration?
Are your "Record Extra Before/After..." settings OK in Preferences?
Is you system clock set correct and displaying the correct time?

If all these are OK, open a terminal and type; sudo shutdown 19:35 -P
{replace 19:35 with a convenient time}

Does your system shutdown at the right time?

---

### Post by feuervogel on 2009-05-20
4 times yes! maybe it's the antenna wich is not receiving the signal constantly and so it's stopping once in a while wich causes the interuption. i will record while watching next time to proove that.

thanks for your help.

---

