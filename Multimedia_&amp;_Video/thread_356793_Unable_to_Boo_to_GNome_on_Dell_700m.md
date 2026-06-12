---
title: "Unable to Boo to GNome on Dell 700m"
date: 2007-02-08
forum: Multimedia &amp; Video
---

### Post by Robotuner on 2007-02-08
Help!  I am trying to adjust my dell 700m resolution by following the steps in:

[http://decompiled.org/howto/slackware700m.html](http://decompiled.org/howto/slackware700m.html)

It seemed really straightforward and the steps are similar to what I have seen in other threads on the subject.  Anyway, in the section on Fixing the Resolution, I pretty much did everything up to:

```
Then I add this to /etc/rc.d/rc.local to make the patch work after every reboot. 

if [ `runlevel | cut -f2 -d' '` -eq 3 ]; then
#runscript
/usr/sbin/855resolution 34 1280 800
fi
if [ `runlevel | cut -f2 -d' '` -eq 5 ]; then
#runscript
/usr/sbin/855resolution 34 1280 800
fi
```

Instead, I just rebooted the machine thinking I was suppose to make the above changes afterwards.  Well, the machine won't boot in gnome, and I am stuck in the terminal mode.  I looked and there isnt' a /etc/rc.d/rc.local on my installation.  Specifically, there isn't a /rc.d/rc.local under the /etc directory.

I have two questions:  Where should I put the above and commands and how do I do it?  Am I suppose to create a file at some location and type that in?  

Thanks.

---

