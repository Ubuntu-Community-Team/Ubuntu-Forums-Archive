---
title: "DaVinci Resolve (Blackmagic) - log4cxx problem"
date: 2017-03-29
forum: Multimedia Software
---

### Post by docdoc2 on 2017-03-29
Finally Resolve is out there for Linux! I followed these instructions to install [https://www.thefanclub.co.za/how-to/how-install-blackmagic-design-davinci-resolve-125-ubuntu-1604-lts](https://www.thefanclub.co.za/how-to/how-install-blackmagic-design-davinci-resolve-125-ubuntu-1604-lts)

But when i want to start, i will get this

```
ActCCMessage Already in Table: Code= 2222, Mode=  0, Level=  0, CmdKey= 8, Option= 0
ActCCMessage Already in Table: Code= c005, Mode= 13, Level=  1, CmdKey= -1, Option= 0
ActCCMessage Already in Table: Code= c006, Mode= 13, Level=  1, CmdKey= -1, Option= 0
ActCCMessage Already in Table: Code= c007, Mode= 13, Level=  1, CmdKey= -1, Option= 0
12.5.5 (#026)
Main thread starts: 12EA5AC0
log4cxx: No appender could be found for logger (Undefined).
log4cxx: Please initialize the log4cxx system properly.

```

I installed liblog4cxx10 via synaptic, but nothing changed.

The software is made for Centos (whatever that is), but i read from several users they were able to run it on Ubuntu.

---

### Post by dj--alex on 2017-05-16
how you install it via Synaptic? 
where you found PPA for log4cxx , it doesn't exist

---

### Post by docdoc2 on 2017-05-26
I didn't find it at all, but the software Davinci Resolve claims it. It is originally made for a Redhat distro, Cent OS, but also works on Ubuntu - not on mine, however.

---

