---
title: "&quot;Sharing&quot; fails, even after samba is installed"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by sexyclient2 on 2009-11-08
So I tried to share a folder (my "Public" folder,) but was prompted to install samba.  After doing so and then restarting I get the following error:
```

Samba's testparm returned error 1: Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
ERROR: lock directory /var/run/samba does not exist
ERROR: pid directory /var/run/samba does not exist

```

I tried "sudo samba restart" but I get the following errors:
```

Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "passdb backend"
Ignoring unknown parameter "passdb backend"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"

```

After manually creating the /var/run/samba folder, I get the following error:
```

'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. Memory allocation error.

```

Any help?  Not that I'm actually expecting any... I can't stop mobile broadband from draining my battery, my bluetooth only works once, empathy and pidgin don't do anything when I try to voice-chat -- and now this.  Why the hell is this version of ubuntu 9.10 not classified as "beta" ??  Ugh... I'm a bit frustrated at the bevy of problems (and lack of support) that I'm encountering with Ubuntu 9.10, just ignore the rant.  

Anyone get at least samba to work in ubuntu 9.10?

---

### Post by peakpc on 2009-11-08
Yes I have done it by running "gksu nautilus" Right mouse on the folder you want to share, go to properties then to the share tab check the appropriate blocks and the create share (if samba is not loaded you will get a prompt to install it and then restart) then just do it again to set the share. This worked for me (easy GUI way, no direct editing of smb.conf necessary).:D

---

### Post by sexyclient2 on 2009-11-08
I followed those very same steps you did (first regularly, then as a super-user with gksu nautilus,)  but I got those error messages...

The first and last messages both appear in the nautilus share window right below the sharing config options, and come with a nice dark-red/brown/burgundy highlight to let me know that things did not go as well for me as they did for you.  The second error message appears when I type "sudo samba restart" in the terminal (as directed by the ubuntu wiki in the event that samba doesn't auto-start.)

---

### Post by Iowan on 2009-11-08
I haven't yet converted to Karmic (lucky me?). but saw a thread that suggested */etc/init.d* had been replaced with  "service" (otherwise, I'd suggest using **/etc/init.d/samba restart**) Do you still get the "lock directory" and "pid directory" errors?

---

### Post by sexyclient2 on 2009-11-08
> **Iowan said:**
> I haven't yet converted to Karmic (lucky me?). but saw a thread that suggested */etc/init.d* had been replaced with  "service" (otherwise, I'd suggest using **/etc/init.d/samba restart**) Do you still get the "lock directory" and "pid directory" errors?

YES! It worked!  I did "sudo /etc/init.d/samba restart" in a terminal fixed everything up :D!
Hopefully samba will start automatically, but if it doesn't I'll just have to make a .sh file and run it at login.  All hope is not lost!  Thanks a million!

---

