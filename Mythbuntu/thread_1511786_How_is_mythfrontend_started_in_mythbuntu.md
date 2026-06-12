---
title: "How is mythfrontend started in mythbuntu"
date: 2010-06-17
forum: Mythbuntu
---

### Post by seppl82 on 2010-06-17
Anyone knows where the autostart of the mythfrontend is configured in mythbuntu.

/THX

---

### Post by David Grigor on 2010-06-17
Have you looking in the mythbuntu control center gui, There should be a checkbox for starting automatically in one of those sections. Of the top of my head thinking it's called something like behavior.

---

### Post by seppl82 on 2010-06-18
Hi,

this is quite clear to me.
Can someone explain more in detail?
I'll try to launch mythtv with different commandline parameters or from a different location (my own cvs build) automatically.

Kind Regards
/Seppl

---

### Post by nickrout on 2010-06-19
take a look at the /usr/bin/mythbuntu script, it's a bash script that calls mythfrontend.real, which is the binary.

Settings are in /etc/mythtv/session-settings

---

### Post by seppl82 on 2010-06-19
Hi Rickout,

thanks a lot for you're reply.
My problem in detail is that i've compiled mythtv from source.
After that it is not starting anymore automatically.
What i've did is changing this file
```
vi /usr/bin/mythfrontend
```

and changed there 

```
/usr/bin/mythfrontend.real 
to
/usr/local/bin/mythfrontend
```

but it is not starting anymore.
Is there a logfile where i can take a look what happend?

---

### Post by tgm4883 on 2010-06-19
MCC just creates a symlink to the autostart folder

```
/usr/share/applications/mythtv.desktop
```

symlinked to

```
/home/$USER/.config/autostart/mythtv.desktop
```

---

### Post by seppl82 on 2010-06-20
Thanks a lot :-)
Now it is 100% clear :-)

---

