---
title: "Net Usershare Returned Error 255"
date: 2009-09-18
forum: Networking &amp; Wireless
---

### Post by Tapas Bose, India on 2009-09-18
Hallo everybody.
Today morning I got an error n my Ubuntu 9.04 showing

There was an error while getting the sharing information.
'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

What does it mean? Is it a serious problem? How to resolve it?
Thanks in advance.

---

### Post by swerdna on 2009-09-19
> **Tapas Bose, India said:**
> Hallo everybody.
Today morning I got an error n my Ubuntu 9.04 showing

There was an error while getting the sharing information.
'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

What does it mean? Is it a serious problem? How to resolve it?
Thanks in advance.

The "usershare" facility is accessible via Nautilus. Sometimes the setup for usershares needs a little tweaking. You can make the missing directory with these commands:
[LIST]
[*]sudo mkdir /var/lib/samba/usershares
[*]sudo chgrp sambashare /var/lib/samba/usershares
[*]sudo chmod 1770 /var/lib/samba/usershares
[/LIST]

You'll also need to check these lines are in the [global] section of the Samba configuration file, smb.conf, which you'll find at /etc/samba/smb.conf:
```
map to guest = Bad User
usershare allow guests = Yes
usershare max shares = 100
usershare owner only = False
```

---

### Post by swerdna on 2009-09-19
Actually, all of the above might be unnecessary if you haven't installed the package nautilus-share which is available in e.g. Syanaptic in System --> administration --> synaptic --> nautilus-share

That might auto configure all of it for you.

---

### Post by Tapas Bose, India on 2009-09-19
> **swerdna said:**
> Actually, all of the above might be unnecessary if you haven't installed the package nautilus-share which is available in e.g. Syanaptic in System --> administration --> synaptic --> nautilus-share

That might auto configure all of it for you.
Thank you swerdna . But I had installed nautilus-share before.

---

### Post by swerdna on 2009-09-19
> **Tapas Bose, India said:**
> Thank you swerdna . But I had installed nautilus-share before.

OK then, execute the three commands, and make sure the four lines are in the [global] stanza of smb.conf.

Also, make sure the group "sambashare" exists and that you are a member of that group. You can check that in the Panel icon --> System --> Administration --> Users and Groups --> Unlock --> Manage groups --> [COLOR="Red"]sambashare[/COLOR] --> Properties.

---

### Post by Tapas Bose, India on 2009-09-19
> **swerdna said:**
> OK then, execute the three commands, and make sure the four lines are in the [global] stanza of smb.conf.

Also, make sure the group "sambashare" exists and that you are a member of that group. You can check that in the Panel icon --> System --> Administration --> Users and Groups --> Unlock --> Manage groups --> [COLOR=Red]sambashare[/COLOR] --> Properties.
Thank you.
In the smb.conf file the lines are not present in global stanza. In authentication stanza the last line consist "map to guest = bad user". 
What should I do? Should I copy the lines given by you into the global stanza and execute the three commands?
Also I am the member of sambashare.

---

### Post by swerdna on 2009-09-19
> **Tapas Bose, India said:**
> Thank you.
In the smb.conf file the lines are not present in global stanza. In authentication stanza the last line consist "map to guest = bad user". 
What should I do? Should I copy the lines given by you into the global stanza and execute the three commands?
Also I am the member of sambashare.
Yep

---

### Post by Tapas Bose, India on 2009-09-19
Thank you. How can I find whether the problem is solve or not?

---

### Post by swerdna on 2009-09-19
> **Tapas Bose, India said:**
> Thank you. How can I find whether the problem is solve or not?

Reboot and test:

Do you still get the error when you do whatever it was that created the error message?
[LIST]
[*]If "no" then problem is solved.
[*]If "yes" then describe in full detail what you do to produce the error.
[/LIST]

---

### Post by Tapas Bose, India on 2009-09-19
Thank you very much. I reboot my computer. But no error is shown. Another thing I want to tell you, the net usershare error was shown for the first time, today. After that, today, I restarted my computer for 3 times, but the error message is not displayed. I think the problem is solved.
 
Also I am facing a problem with my firefox for one month or over. I had enabled "Show text during boot" option from System -> Administration -> Start up Manager. From that text I saw some failure of loading of firefox 3.5. Like:

*Skipped: /etc/apparmor.d/usr.bin.firefox-3.5
Error: #include <abstractions/private-data> not found at line 81 in /etc/apparmor.d/usr.bin.firefox-3.5
Error: #include <abstractions/ubuntu-mail> not found at line 166 in /etc/apparmor.d/usr.bin.firefox-3.5
Error: #include <abstractions/ubuntu-console-email> not found at line 167 in /etc/apparmor.d/usr.bin.firefox-3.5
Error: #include <abstractions/ubuntu-gnome-terminal>  not found at line 167 in /etc/apparmor.d/usr.bin.firefox-3.5
*Failure: /etc/apparmor.d/usr.bin.firefox-3.5 failed to load                      [fail]

I have uninstall and again install firefox-3.5 for 3 times. But the error message is still displayed during shut down and startup.

---

### Post by swerdna on 2009-09-19
> **Tapas Bose, India said:**
> Thank you very much. I reboot my computer. But no error is shown. Another thing I want to tell you, the net usershare error was shown for the first time, today. After that, today, I restarted my computer for 3 times, but the error message is not displayed. I think the problem is solved.
It is fixed -- well done

> **Tapas Bose, India said:**
> 
I have uninstall and again install firefox-3.5 for 3 times. But the error message is still displayed during shut down and startup.

I can't help you with this. Seek help in the forum "General Help". Start a new thread there. Good luck.

---

### Post by cyjambo on 2010-06-25
> **swerdna said:**
> The "usershare" facility is accessible via Nautilus. Sometimes the setup for usershares needs a little tweaking. You can make the missing directory with these commands:
[LIST]
[*]sudo mkdir /var/lib/samba/usershares
[*]sudo chgrp sambashare /var/lib/samba/usershares
[*]sudo chmod 1770 /var/lib/samba/usershares
[/LIST]

You'll also need to check these lines are in the [global] section of the Samba configuration file, smb.conf, which you'll find at /etc/samba/smb.conf:
```
map to guest = Bad User
usershare allow guests = Yes
usershare max shares = 100
usershare owner only = False
```

The first 3 commands did it (didn't even have to log out) , thanks a lot :)
I uninstalled samba completely before and reinstalled it, and folders were not created...
This did the job.
Nice info.


Peace

---

### Post by swerdna on 2010-06-25
Glad to hear.

---

