---
title: "[SOLVED] Powering off computer with remote power button"
date: 2007-10-15
forum: Mythbuntu
---

### Post by antoniuk on 2007-10-15
Is this possible?

Using the power button to execute a script to turn off the box? I know turning it on would be an exercise in futility but being able to fire off a bash script to properly shutdown the system would be very cool indeed

This is for the grey style pvr350 remote

[http://www.mythtv.org/wiki/index.php/PVR-350_Remote_Quick_Guide](http://www.mythtv.org/wiki/index.php/PVR-350_Remote_Quick_Guide)

---

### Post by antoniuk on 2007-10-15
What I am assuming is I need to startup irexec in daemon mode, add the ability to have my mythtv account run shutdown elevated from editing sudouser (or users I forget which) then add code in .lircrc to have irexec run shutdown

would something like that work?

---

### Post by superm1 on 2007-10-15
Oh yeah.  This is definitely possible.  I will warn though, it becomes very easy to "accidentally" turn off the box when you don't want to.

This is the easiest way (I think):

First set the /sbin/shutdown SUID (this lets you issue a shutdown without needing to use sudo)
See this post for info on how to do this:
[http://ubuntuforums.org/showpost.php?p=430459&postcount=3](http://ubuntuforums.org/showpost.php?p=430459&postcount=3)


Next, you need to **add** an additional command to your ~/.lircrc

```
begin
     prog = irexec
     button = power
     config = shutdown -h now
end
```

That button may be a little different, check your /etc/lirc/lircd.conf to verify that is what your power button is called.

Log out and back in.  Irexec is automatically started when you log in.  

Press your button and go. :)

---

### Post by antoniuk on 2007-10-15
Perfect! Worked like a charm!

I have to say your myth ubuntu project here has turned what I thought was going to be a several weekend hack job into a casual Sunday night  setup.

thank you for making my weekend :)

Mythbuntu at least for me worked flawlessly once I tweaked the few settings that needed tweaking for my system. I can now watch tv from my computer room.

---

### Post by drarmi on 2007-10-25
Very useful! I used ubuntu earlier and there I alwasy got the shutdown dialog when pressing the Power button. But now when I am running Mythbuntu I was missing that ... 

No this is not a problem anymore.

Thanks!!

---

### Post by jackelmatador on 2007-10-26
For the really lazy, if you want a way to turn you TV back on using a remote...

[http://www.simerec.com/](http://www.simerec.com/)

I love it!

---

