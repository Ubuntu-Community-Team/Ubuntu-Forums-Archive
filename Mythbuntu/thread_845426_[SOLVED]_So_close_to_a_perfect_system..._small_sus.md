---
title: "[SOLVED] So close to a perfect system... small suspend issue"
date: 2008-06-30
forum: Mythbuntu
---

### Post by sebrock on 2008-06-30
I almost have my system-of-dreams finished now. Just a tiny little bit left and I hope anyone can give me a helping advice.

My three small issues all depend on the the same thing: suspend-to-ram. Now I know this sound like a no-go, but I'm fairly confident we will work this one out because I can manually get it to work. So please continue reading:

What I need to do is to stop LCDd and lirc at suspend and then restart it upon resume. I tried putting them into */etc/defaults/acpi-support* under services but I'm not even sure mythbuntu uses that file. Doesnt seem like that. I also tried to unload modules *lirc_imon* and *lirc_dev* (in that order) in the same file however upon resume lirc_imon.c keeps flooding syslog that it cant connect to the device. (Hence I need to shut it down and fresh restart it when suspending)

if I unload everything manually it of cause works.

How do I get this automated in the scripts?

---

### Post by superm1 on 2008-07-01
You'll need to add stuff into /etc/pm.  Those are pm-utils config files.

---

### Post by sebrock on 2008-07-01
I see, so */etc/defaults/acpi-support* is not used in mythbuntu at all?

Now, I understand that I should use the sleep.d directory and put my init-scripts in there. But what do I do with modules that needs to be unloaded/reloaded?

Regards

---

### Post by superm1 on 2008-07-01
> **sebrock said:**
> I see, so */etc/defaults/acpi-support* is not used in mythbuntu at all?

Now, I understand that I should use the sleep.d directory and put my init-scripts in there. But what do I do with modules that needs to be unloaded/reloaded?

Regards
This was an oversight in normal Ubuntu too.  acpi-support is deprecated, but no one made a good effort to indicate this.

If you create a script and make it executable, it's something like 

SUSPEND_MODULES=my_favorite_module

inside the script and that's it.

---

### Post by sebrock on 2008-07-01
Nope I did not udnerstand how to use sleep.d directory. Modules seems to work as I wanted now. But how to add LCDd and lirc to be stopped at suspend and then started at resume.

a script with simply "/etc/init.d/LCDd stop" will only stop it. And copying the init.d-script to the sleep.d dir did not work either.

Thanks

***EDIT***
I solved it with a case script:

```

#!/bin/bash
case $1 in
    hibernate)
        echo "Suspending to disk"
        /etc/init.d/LCDd stop
        /etc/init.d/lirc stop
       ;;
    suspend)
        echo "Suspend-to-RAM"
        /etc/init.d/LCDd stop
        /etc/init.d/lirc stop
        ;;
    thaw)
        echo "Resuming from disk"
        /etc/init.d/lirc start
        /etc/init.d/LCDd start
        ;;
    resume)
        echo "Resume-from-RAM"
        /etc/init.d/lirc start
        /etc/init.d/LCDd start
        ;;
    *)  echo "Wrong argument"
        ;;
esac

```

Stuff is great! No I have the killer frontend I always wanted :D

---

