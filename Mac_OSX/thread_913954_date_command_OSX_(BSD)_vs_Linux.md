---
title: "date command: OSX (BSD) vs Linux"
date: 2008-09-08
forum: Mac OSX
---

### Post by nublaii on 2008-09-08
Hi, I'm trying to get BSD's [FONT="Courier New"]date[/FONT] command functionality on ubuntu. With BSD's [FONT="Courier New"]date[/FONT] I can do date conversions on the fly... can't seem to do that on ubuntu.

I'm specifically talking about the [FONT="Courier New"]-f[/FONT] flag on BSD's [FONT="Courier New"]date[/FONT] command.

Couple of urls to check it out

[BSD's date]("http://nixdoc.net/man-pages/FreeBSD/date.1.html")

[Ubuntu's date]("http://manpages.ubuntu.com/manpages/intrepid/man1/date.html")

---

### Post by ilrudie on 2008-09-08
[]("http://manpages.ubuntu.com/manpages/intrepid/man1/date.html")You don't need a flag with Ubuntu' date.

>date +%Y 
2008

---

### Post by nublaii on 2008-09-08
> **ilrudie said:**
> []("http://manpages.ubuntu.com/manpages/intrepid/man1/date.html")You don't need a flag with Ubuntu' date.

>date +%Y 
2008

I have a bunch of dates formatted like this:

```

day/month/year
25/12/08
22/11/07
22/08/04
08/03/02
```

And I want to format those dates, not the current time.

I just can't figure out how to pass the format I use to the date command...

---

### Post by ilrudie on 2008-09-08
You can use awk to do something like this:

```

>cat timetest
day/month/year
25/12/08
22/11/07
22/08/04
08/03/02

>awk -F "/" '{printf("%s-%s-%s\n", $3,$2,$1)}' timetest
year-month-day
08-12-25
07-11-22
04-08-22
02-03-08

```

---

### Post by airbonejerm on 2009-01-10
you can use awk for certain things, but that doesn't change the original question for getting a bsd-like date on ubuntu.. i'm honestly baffled by the lack of date functionality.. the above example lends itself easily to awk, but what about transforming a date code like

20081201000551  
YYYYmmDDHHMMSS  to epoch time?  in bsd date it's

date -j -f "%Y%m%d%H%M%S" 20081201000551 "+%s"

or to translate it to a normalish date 

TIME=$(date -j -f "%Y%m%d%H%M%S" 20081201000551 "+%a %b %d %T %Z %Y")

it's clean, simple, no crazy parsing and splitting necessary, all in one command

the other extremely useful thing that bad date does is midbogglingly easy date math/manipulation

date -v1d -v+1m -v-1d -v-fri
displays the last friday of the month as a normal date/time

date -v+1m -v1d -v0M -v0H -v0S +%s
shows me midnight, the first day of next month, in epoch time

it's amazingly flexible and useful and free as in speech and beer (bsd license?). 

so.. anyone have a good solution for getting on ubuntu? :)

---

### Post by lswb on 2009-01-10
I don't know how to specify the input format either, but date -d will convert a date string from certain input formats.

example
```

$ date -d 20081211
Thu Dec 11 00:00:00 EST 2008

~$ date -d 1/3/09
Sat Jan  3 00:00:00 EST 2009

```

---

