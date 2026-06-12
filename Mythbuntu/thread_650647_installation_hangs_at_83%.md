---
title: "installation hangs at 83%"
date: 2007-12-26
forum: Mythbuntu
---

### Post by jfix on 2007-12-26
Hi, I am about to install Mythbuntu 7.10 frontend on my current frontend machine.  It is a Asus Pundit-R350, and I am installing on to a 4 GB usb stick (no moving thus noisy parts), from the downloaded cdrom image.

I am doing the advanced, Frontend-only installation, using opensource ati driver option, X10 remote, and most plugins.

At 83% "Configuring mythtv", it just doesn't continue.  The machine is still available, I have a terminal open and am tailing -f syslog, but nothing happens, also no error messages.

as regards space on the memory stick:

$ df -h
Filesystem                   Size   Used  Avail  Use%  Mounted on
/dev/sda1                    3.5G  1.2G   2.1G  37%    /target

In the syslog, I see the user created and added to a number of groups, a number of services created (ntp, mysql, samba, apache2, mythtv-backend??? I thought I selected the frontend installation only, ssh)

I read elsewhere on this forum that another user had it hang at 83% for two hours, but here it's almost all day long.

I would be interested to know what is supposed to happen at this stage, because I could do the missing steps manually.

Thanks for any pointers, you'll be credited for saving the family peace :)

cheers,
Jakob.

---

### Post by superm1 on 2007-12-26
> **jfix said:**
> Hi, I am about to install Mythbuntu 7.10 frontend on my current frontend machine.  It is a Asus Pundit-R350, and I am installing on to a 4 GB usb stick (no moving thus noisy parts), from the downloaded cdrom image.

I am doing the advanced, Frontend-only installation, using opensource ati driver option, X10 remote, and most plugins.

At 83% "Configuring mythtv", it just doesn't continue.  The machine is still available, I have a terminal open and am tailing -f syslog, but nothing happens, also no error messages.

as regards space on the memory stick:

$ df -h
Filesystem                   Size   Used  Avail  Use%  Mounted on
/dev/sda1                    3.5G  1.2G   2.1G  37%    /target

In the syslog, I see the user created and added to a number of groups, a number of services created (ntp, mysql, samba, apache2, mythtv-backend??? I thought I selected the frontend installation only, ssh)

I read elsewhere on this forum that another user had it hang at 83% for two hours, but here it's almost all day long.

I would be interested to know what is supposed to happen at this stage, because I could do the missing steps manually.

Thanks for any pointers, you'll be credited for saving the family peace :)

cheers,
Jakob.

Did you hit the button to "test" your connection in the installer?  It *must* have access to your backend during installation to set a few defaults on the SQL server.  That's what that button is there for.

---

### Post by jfix on 2007-12-26
superm1,

> **superm1 said:**
> Did you hit the button to "test" your connection in the installer?  It *must* have access to your backend during installation to set a few defaults on the SQL server.  That's what that button is there for.

sure, I did that, and it reported success.

what's supposed to happen at this stage?  is there some documentation on the inner workings of the mythbuntu install procedure?  or is there some code to look at?

I did the install procedure several times, and it always hang there.

thanks anyway.

cheers,
Jakob.

---

### Post by superm1 on 2007-12-26
> **jfix said:**
> superm1,



sure, I did that, and it reported success.

what's supposed to happen at this stage?  is there some documentation on the inner workings of the mythbuntu install procedure?  or is there some code to look at?

I did the install procedure several times, and it always hang there.

thanks anyway.

cheers,
Jakob.
Can you post /var/log/syslog?   I can help you understand what is happening there.

---

### Post by jfix on 2007-12-26
i put the log file here because it's too big as an attachment for this forum:
[URL="http://jakob.free.fr/teevee.syslog.txt"]http://jakob.free.fr/teevee.syslog.txt
[/URL]

The only potentially interesting errors start appearing here:

```

Dec 26 16:46:35 ubuntu ubiquity: /proc/misc: No entry for device-mapper found
Dec 26 16:46:35 ubuntu ubiquity: 
Dec 26 16:46:35 ubuntu ubiquity: Is device-mapper driver missing from kernel?
Dec 26 16:46:35 ubuntu ubiquity:
Dec 26 16:46:35 ubuntu ubiquity: Failure to communicate with kernel device-mapper driver.
Dec 26 16:46:35 ubuntu ubiquity:

```

but as the installer continued I didn't think anything about it.  And I wouldn't know how to fix these errors anyway.

thanks again for looking into this issue.  I can provide more info if needed.


cheers,
Jakob.

---

### Post by superm1 on 2007-12-26
> **jfix said:**
> i put the log file here because it's too big as an attachment for this forum:
[URL="http://jakob.free.fr/teevee.syslog.txt"]http://jakob.free.fr/teevee.syslog.txt
[/URL]

The only potentially interesting errors start appearing here:

```

Dec 26 16:46:35 ubuntu ubiquity: /proc/misc: No entry for device-mapper found
Dec 26 16:46:35 ubuntu ubiquity: 
Dec 26 16:46:35 ubuntu ubiquity: Is device-mapper driver missing from kernel?
Dec 26 16:46:35 ubuntu ubiquity:
Dec 26 16:46:35 ubuntu ubiquity: Failure to communicate with kernel device-mapper driver.
Dec 26 16:46:35 ubuntu ubiquity:

```but as the installer continued I didn't think anything about it.  And I wouldn't know how to fix these errors anyway.

thanks again for looking into this issue.  I can provide more info if needed.


cheers,
Jakob.
In reading this log, I suspect there was a partition not cleared out before installation?  Is this correct?

Additionally, at that step, it is attempting to contact your mysql server to setup the theme.

---

### Post by jfix on 2007-12-27
> **superm1 said:**
> In reading this log, I suspect there was a partition not cleared out before installation?  Is this correct?

Additionally, at that step, it is attempting to contact your mysql server to setup the theme.

as regards the partition, I did not reformat the memory stick in between installations, that's correct.

as regards the connexion with the server that works (as tested at the beginning of the installation) and shown by the fact that I scp'ied the syslog to this machine that I put up on my site.

I'll reformat the stick, and start over hoping this may fix it.  I'll report back.

cheers,
Jakob.

---

### Post by jfix on 2007-12-27
ok, here's an update:  I have tried installing the system onto a normal hard drive (just to make sure it's not something to do with the memory stick), **but installation again hangs at 83%**.

now, here's some disclosure:  the backend that's running on the network is not one that has been installed using mythbuntu but a vanilla debian package on a debian server.  does this has an importance?

does mythbuntu expects something special in the mythconverg database (that I could add manually if necessary)?

also, I don't want to replace the current (working) backend installation without knowing that the frontend installation will be 100% ok, too.

again, does somebody know what **exactly** happens at 83% during the advanced, frontend-only installation?

the installation entries in the syslog stop at
```

...
Dec 27 18:20:52 ubuntu mythbuntu:      /etc/rc5.d/S20ssh -> ../init.d/ssh

```

after that it's just the usual --- MARK --- and renewing of the dhcp ip address etc.

thanks in advance.

cheers,
Jakob.

---

### Post by superm1 on 2007-12-27
Jakob,

At that point, this script is running:

/usr/share/ubiquity/apply-type

fix_init_scripts() has just completed

setup_theme
and 
grabuser

are about to run.  Odds are it is stuck on setup_theme.  It contacts your mysql server at this point using the information that you verified earlier in the installer.

---

### Post by jfix on 2007-12-27
superm1,

thanks a lot for indicating the script where the install hangs.

it made me check the database server locally, and lo!, I found there was no space left on the hard disk, due to some huge mysql log files ...  as soon as I had them deleted the process continued w/o problems!

I am re-running it right now with my initial configuration ... and it looks good!

So, in summary: Apparently, although the database was unable to service a request, the connection test returned success.  maybe, something could be done to find out more about the database server?  just an idea.

Also, at the 83% point, I don't know what the return code would be for a database that cannot service a request because there's no space left on the hard disk, but that could be one thing that could be improved.

Otherwise, let me say that mythbuntu is one great piece of software that hugely facilitates the installation of mythv (and I've done it the hard way a couple of years ago)!

Thanks a lot , superm1 (I've seen your name all over the installation code :))

cheers,
Jakob.

---

### Post by superm1 on 2007-12-27
> **jfix said:**
> superm1,

thanks a lot for indicating the script where the install hangs.

it made me check the database server locally, and lo!, I found there was no space left on the hard disk, due to some huge mysql log files ...  as soon as I had them deleted the process continued w/o problems!

I am re-running it right now with my initial configuration ... and it looks good!

So, in summary: Apparently, although the database was unable to service a request, the connection test returned success.  maybe, something could be done to find out more about the database server?  just an idea.

Also, at the 83% point, I don't know what the return code would be for a database that cannot service a request because there's no space left on the hard disk, but that could be one thing that could be improved.

Otherwise, let me say that mythbuntu is one great piece of software that hugely facilitates the installation of mythv (and I've done it the hard way a couple of years ago)!

Thanks a lot , superm1 (I've seen your name all over the installation code :))

cheers,
Jakob.
No prob.

This is something that can probably be improved, you are right.

Currently it just checks if a table can be SELECTed using that username and password.  Perhaps if instead it tries to write a temporary value and remove it this would work better.  Can you possibly take a few moments to file a bug against the mythbuntu project on launchpad regarding this?  It will be a little bit until I can get to it.

Or even better, you can see the code used for the tester in ubiquity's mythbuntu_ui.py file.  do_connection_test I think was the function I wrote.

If you want to improve upon it, and make it more robust, feel free :)

---

### Post by jfix on 2007-12-27
superm1,

will do for the bug report, not sure about improving the python code.  I'll look into it.

thanks again!

cheers,
Jakob.

PS: Will probably be back asking for help when moving my backend to mythbuntu ... :)

---

### Post by jfix on 2007-12-27
just filed the bug report, it's here:

[https://bugs.launchpad.net/mythbuntu/+bug/178987](https://bugs.launchpad.net/mythbuntu/+bug/178987)

cheers,
Jakob.

---

