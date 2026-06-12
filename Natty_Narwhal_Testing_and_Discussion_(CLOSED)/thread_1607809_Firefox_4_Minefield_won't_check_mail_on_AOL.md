---
title: "Firefox 4 Minefield won't check mail on AOL"
date: 2010-10-28
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by jerrylamos on 2010-10-28
Yesterday the "dread update" struck again, this time on Firefox 4 Minefield on Natty.  Yahoo mail works.  Ubuntu forums work.  Youtube works.
AOL mail is missing the top banner including the check mail tab, and selecting "incoming mail" does nothing.  Worked fine before the "update".

I did open launchpad bug #667367 because ubuntu-bug fails:

jerry@Thinkpad:~$ ubuntu-bug firefox
Traceback (most recent call last):
  File "/usr/share/apport/apport-gtk", line 368, in <module>
    app.run_argv()
  File "/usr/lib/python2.6/dist-packages/apport/ui.py", line 558, in run_argv
    return self.run_report_bug()
  File "/usr/lib/python2.6/dist-packages/apport/ui.py", line 374, in run_report_bug
    self.collect_info(symptom_script)
  File "/usr/lib/python2.6/dist-packages/apport/ui.py", line 785, in collect_info
    self.crashdb = get_crashdb(None, self.report['CrashDB'])
  File "/usr/lib/python2.6/dist-packages/apport/crashdb.py", line 536, in get_crashdb
    db = settings['databases'][name]
KeyError: 'ubuntu-mozilla-ppa-bugs'

Firefox 3 still working O.K. on same ubuntu install.

Jerry

---

### Post by Starks on 2010-10-28
Not to judge you, by why not create a gmail account and forward all of your AOL mail to it?

---

### Post by Merk42 on 2010-10-28
> **Starks said:**
> Not to judge you, by why not create a gmail account and forward all of your AOL mail to it?
Well Gmail doesn't seem to work in Firefox 4 beta 6 (on Windows, haven't used it in Ubuntu)

---

### Post by jerrylamos on 2010-10-28
> **Starks said:**
> Not to judge you, by why not create a gmail account and forward all of your AOL mail to it?

I do Yahoo mail, AOL (AIM) mail, gmail and other ordinary user stuff looking for Ubuntu bugs.  This one looks like Firefox 4.

No mail on local pc because I use 4 test pc's as well as my wife's two.  She uses XP because there isn't any linux Dreamweaver to support the two websites she maintains.  Besides Dreamweaver is $$$ and she has it for XP already.

Jerry

---

### Post by Starks on 2010-10-28
If all else fails, use Thunderbird or Evolution.

---

### Post by jerrylamos on 2010-10-28
> **Starks said:**
> If all else fails, use Thunderbird or Evolution.

Well, currently I use the Firefox 3.6 that comes with Natty where it will work, and Opera where Firefox won't.

Jerry

---

### Post by dext on 2010-10-29
> **jerrylamos said:**
> Well, currently I use the Firefox 3.6 that comes with Natty where it will work, and Opera where Firefox won't.

Jerry

have you tried 4.0 beta8 nightly?

---

### Post by Frogs Hair on 2010-10-29
I had trouble with AOL Radio on Minefeild , It worked fine on Namoroka , Opera , and IE 9 beta. The page would not render properly and I never resolved it and that was the daily build.

---

### Post by jerrylamos on 2010-10-30
> **dext said:**
> have you tried 4.0 beta8 nightly?

Frog's Hair post sounds similar to my experience (There are frogs in our pond all must be clean shaven.)  The top of the AOL page doesn't resolve, links on bicycling.com don't, ... but these do work on Chromium and Opera so I blame Firefox & Firefox 4 (updated).

I haven't found out how to post bugs on Firefox 4 yet as in the first post on this thread.  I'd rather use applications that come with Ubuntu but if it doesn't work I'll use an alternative.  That doesn't help Ubuntu debug tho.

Jerry

---

### Post by plun on 2010-10-30
> **dext said:**
> have you tried 4.0 beta8 nightly?

If you are running Ubuntu and Natty the best way is to use the Ubuntu Mozilla Daily ppa.

[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)

> For questions and bugs with software in this archive, please contact <email address hidden> or visit **#ubuntu-mozillateam on freenode**.

Firefox 4 is also delayed...
[http://groups.google.com/group/mozilla.dev.planning/browse_thread/thread/8bf881e3ba019bd5?pli=1](http://groups.google.com/group/mozilla.dev.planning/browse_thread/thread/8bf881e3ba019bd5?pli=1)

New timetable:
[https://wiki.mozilla.org/Firefox/4/Beta](https://wiki.mozilla.org/Firefox/4/Beta)

---

### Post by dext on 2010-10-30
yeah i knew firefox4 was delayed, there will be 2 more beta's followed by a RC in early 2011

---

### Post by bikeboy on 2010-11-02
Try setting the 'jit' chrome settings to false in about:config. That should at least tell you if it's an issue with the javascript engine changes.

---

### Post by knarf on 2010-11-02
> **jerrylamos said:**
> I haven't found out how to post bugs on Firefox 4 yet as in the first post on this thread

Just go to the related page in launchpad:

[https://bugs.launchpad.net/ubuntu-mozilla-ppa-bugs/+filebug](https://bugs.launchpad.net/ubuntu-mozilla-ppa-bugs/+filebug)

---

