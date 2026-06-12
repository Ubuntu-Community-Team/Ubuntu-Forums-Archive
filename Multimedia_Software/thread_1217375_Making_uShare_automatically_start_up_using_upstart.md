---
title: "Making uShare automatically start up using upstart"
date: 2009-07-19
forum: Multimedia Software
---

### Post by CookieNinja on 2009-07-19
As I understand it, it's a common issue that ushare will not automatically start up after it's installed. Some "fixes" here have mentioned messing about with rc.local to get it working, but some people might be interested in how I have got it working, using upstart rather than the "old school" system for starting up services.

All I did was create a file in /etc/event.d/  called ushare and put the follow text into that file:

```

start on stopped rc2
start on stopped rc3
start on stopped rc4
start on stopped rc5

stop on runlevel 0
stop on runlevel 1
stop on runlevel 6

script
ushare
end script

```

And that is it, there is nothing more to do. Hopefully anyone reading this knows enough to know how to create that file using sudo so that it is owned by root ... because normal users cannot write to the location that file needs to be in.

Ushare should be pretty much the last thing that starts when Ubuntu boots up, because it only starts when rc2 ends. It also means that it starts whenever the system is rebooting or in single user mode.

I'm no whizz on how upstart works, in fact I've only just learned enough to make this work for me, so if someone wants to complicate this and make it better ... feel free and post your improvements back to this thread.

Also, if anyone cannot make this work for them, let me know and I'll see if I can help.

---

