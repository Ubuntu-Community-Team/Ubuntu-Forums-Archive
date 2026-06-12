---
title: "Tuners Not Initializing on Boot"
date: 2009-11-01
forum: Mythbuntu
---

### Post by sgunther on 2009-11-01
I just upgraded to Mythbuntu 9.10 today.  I am getting the error on boot ```
"Error: MythTV is using all inputs, buy there are no active recordings?"
```Restarting the backend fixes it.  In the forums there is a reference to this error only for the HDHomerun, I have 2 PVR-150s and a PVR-500.  Has anyone seen this condition where mythtv-backend boots prior to the local tuners being ready?  In 9.10 where can one change the boot order for the mythtv-backend service?

-sgunther

---

### Post by alexyz on 2009-11-09
I've been running fine for a week but saw this after a reboot.  I've previously rebooted without problem.  Restarting the backend fixed it.  Maybe a timing issue?  Possibly related posts:

[http://ubuntuforums.org/showthread.php?t=1249208](http://ubuntuforums.org/showthread.php?t=1249208)

[http://ubuntuforums.org/showthread.php?t=1290647](http://ubuntuforums.org/showthread.php?t=1290647)

edit:  in addition to the tuner error in backend log, and similar error when you try to watch live TV - this also causes ALL recording rules to disappear.  So all your upcoming recordings are gone.  (huh?  that should really be handled differently.)  Everything reappears when you fix the tuner problem.

---

### Post by sgunther on 2009-11-09
I wanted an elegant way to fix this by having the mythtv-backend process wait until the tuners had initialized but I could not figure out a clean way.  I did come up with a method that will guarantee the backend always comes up for me but occasionally the fronend will need to be rebooted.  At least this way you will get your recordings.


Here is what I did;

```
sudo nano /etc/init/mythtv-backend.conf
```


Find;
```
script
        test -f /etc/default/mythtv-backend && . /etc/default/mythtv-backend ||$
        exec /bin/su -c "/usr/bin/mythbackend $ARGS" $USER
end script
```


And Chnage To;
```
script
        sleep 15
        test -f /etc/default/mythtv-backend && . /etc/default/mythtv-backend ||$
        exec /bin/su -c "/usr/bin/mythbackend $ARGS" $USER
end script
```

The sleep value is customizable, I found that 15 seconds guaranteed a clean boot for me.

Note: This is only applicable to 0.22 based systems running on the 9.10 distrobution as it is now using upstart.

---

