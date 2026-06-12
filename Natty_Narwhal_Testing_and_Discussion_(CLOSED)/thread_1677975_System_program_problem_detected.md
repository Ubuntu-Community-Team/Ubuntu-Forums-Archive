---
title: "System program problem detected"
date: 2011-01-29
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Universal344 on 2011-01-29
I am getting an error message in Natty that comes up in a GTK popup window with no title saying a system program problem has been detected.  It then asks if I want to report the problem or cancel.  Is there a way to tell what process has created this window or some other way to gauge its origin and legitimacy?

---

### Post by sgage on 2011-01-29
That's a great question - I'm getting bunches of these messages. Yet things just keep working, regardless. I'd be interested to know what they are all about.

---

### Post by vmonkey on 2011-01-29
I think it is current problem of most users (testers). Just click report bug and you will see what was the problem.

---

### Post by Universal344 on 2011-01-29
hmmm... okay the only reason I found it odd was because they were completely generic.  It didn't give the name of the program or any details on what happened.

---

### Post by jerrylamos on 2011-01-29
> **vmonkey said:**
> I think it is current problem of most users (testers). Just click report bug and you will see what was the problem.

vmonkey,

I did click on report, which promptly says it can't report because of some obsolete packages.  This is an absolutely fresh install from the latest CD build, 27 January.  That means the latest CD Build is being shipped with obsolete packages and can't report bugs.  Well, that's one way to reduce the number of new bugs posted to Launchpad.

Jerry

p.s.  I did look in /var/log/crash and there is a report there.  I've tried posting a launchpad bug and attaching the crash report, and the developers said they couldn't use a crash report.

---

### Post by cariboo on 2011-01-29
Use ubuntu-bug to report the problem, use whatever package the crash report was for.

```
ubuntu-bug <package-name>
```

---

### Post by jerrylamos on 2011-01-29
> **cariboo907 said:**
> Use ubuntu-bug to report the problem, use whatever package the crash report was for.

```
ubuntu-bug <package-name>
```
Cariboo, I did enter ubuntu-bug evince which ran.  Ubuntu-bug doesn't seem to attach the evince crash report.

Jerry

---

