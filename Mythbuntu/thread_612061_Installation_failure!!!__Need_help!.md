---
title: "Installation failure!!!  Need help!"
date: 2007-11-13
forum: Mythbuntu
---

### Post by kingjos on 2007-11-13
Hi everyone,
I just stumbled across the mythbuntu project and was very interested in using it for my frontend only machine.  I was able to get through the installation wizard but once it got to about 85% complete of the installation a dialog window would come up saying that the installation failed.  I'm wondering if someone has any ideas as to why this might be happening or refer to someone who could help me out with this problem?

thanks in advance:

---

### Post by superm1 on 2007-11-13
What options did you choose?  Did you remember to fill in ALL the dialogs with the mysql information?

Can you post the backtrace?

---

### Post by kingjos on 2007-11-13
This is the  error message that I get.

any help would great !

We're sorry; the installer crashed. Please file a new bug report at [https://launchpad.net/ubuntu/+source/ubiquity/+filebug](https://launchpad.net/ubuntu/+source/ubiquity/+filebug) (do not attach your details to any existing bug) and a developer will attend to the problem as soon as possible. To help the developers understand what went wrong, include the following detail in your bug report, and attach the files /var/log/syslog and /var/log/partman:

Traceback (most recent call last):
  File "/usr/lib/ubiquity/bin/ubiquity", line 212, in <module>
    main()
  File "/usr/lib/ubiquity/bin/ubiquity", line 207, in main
    install(args[0])
  File "/usr/lib/ubiquity/bin/ubiquity", line 65, in install
    ret = wizard.run()
  File "/usr/lib/ubiquity/ubiquity/frontend/mythbuntu_ui.py", line 252, in run
    self.progress_loop()
  File "/usr/lib/ubiquity/ubiquity/frontend/mythbuntu_ui.py", line 330, in progress_loop
    (ret, realtb))
RuntimeError: Install failed with exit code 1
Traceback (most recent call last):
  File "/usr/share/ubiquity/mythbuntu_install.py", line 288, in <module>
    install.run()
  File "/usr/share/ubiquity/mythbuntu_install.py", line 100, in run
    self.configure_mythbuntu()
  File "/usr/share/ubiquity/mythbuntu_install.py", line 179, in configure_mythbuntu
    raise InstallStepError("MythbuntuApply Debconf Xfer failed with code %d" % ret)
InstallStepError: MythbuntuApply Debconf Xfer failed with code 255

---

### Post by superm1 on 2007-11-13
> **kingjos said:**
> This is the  error message that I get.

any help would great !

We're sorry; the installer crashed. Please file a new bug report at [https://launchpad.net/ubuntu/+source/ubiquity/+filebug](https://launchpad.net/ubuntu/+source/ubiquity/+filebug) (do not attach your details to any existing bug) and a developer will attend to the problem as soon as possible. To help the developers understand what went wrong, include the following detail in your bug report, and attach the files /var/log/syslog and /var/log/partman:

Traceback (most recent call last):
  File "/usr/lib/ubiquity/bin/ubiquity", line 212, in <module>
    main()
  File "/usr/lib/ubiquity/bin/ubiquity", line 207, in main
    install(args[0])
  File "/usr/lib/ubiquity/bin/ubiquity", line 65, in install
    ret = wizard.run()
  File "/usr/lib/ubiquity/ubiquity/frontend/mythbuntu_ui.py", line 252, in run
    self.progress_loop()
  File "/usr/lib/ubiquity/ubiquity/frontend/mythbuntu_ui.py", line 330, in progress_loop
    (ret, realtb))
RuntimeError: Install failed with exit code 1
Traceback (most recent call last):
  File "/usr/share/ubiquity/mythbuntu_install.py", line 288, in <module>
    install.run()
  File "/usr/share/ubiquity/mythbuntu_install.py", line 100, in run
    self.configure_mythbuntu()
  File "/usr/share/ubiquity/mythbuntu_install.py", line 179, in configure_mythbuntu
    raise InstallStepError("MythbuntuApply Debconf Xfer failed with code %d" % ret)
InstallStepError: MythbuntuApply Debconf Xfer failed with code 255
If you could go a little further and post your /var/log/syslog after that crash as well as any options you chose.

---

### Post by kingjos on 2007-11-13
ok so i figured out my  first problem with installing my frontend system but now i'm having problems starting my backend.  so the output i get when trying to start my backend server is this:

joshua@masterbackend:~$ sudo mythbackend
2007-11-13 19:42:07.914 Using runtime prefix = /usr
2007-11-13 19:42:07.927 New DB connection, total: 1
2007-11-13 19:42:07.932 Connected to database 'mythconverg' at host: localhost
2007-11-13 19:42:07.934 Current Schema Version: 1160
Starting up as the master server.
2007-11-13 19:42:07.965 New DB connection, total: 2
2007-11-13 19:42:07.965 Connected to database 'mythconverg' at host: localhost
2007-11-13 19:42:07.967 EITHelper: localtime offset -6:00:00 
2007-11-13 19:42:07.969 New DB connection, total: 3
2007-11-13 19:42:07.970 Connected to database 'mythconverg' at host: localhost
2007-11-13 19:42:08.145 EITHelper: localtime offset -6:00:00 
2007-11-13 19:42:08.314 New DB scheduler connection
2007-11-13 19:42:08.314 Connected to database 'mythconverg' at host: localhost
QServerSocket: failed to bind or listen to the socket
2007-11-13 19:42:08.320 MediaServer::HttpServer Create Error
2007-11-13 19:42:08.320 Main::Registering HttpStatus Extension
2007-11-13 19:42:08.321 mythbackend version: 0.20.20070821-1 [www.mythtv.org](www.mythtv.org)
2007-11-13 19:42:08.321 Enabled verbose msgs:  important general
2007-11-13 19:42:08.322 AutoExpire: Found 2 recorders w/max rate of 144 MiB/min
2007-11-13 19:42:08.322 AutoExpire: Required Free Space: 3.1 GB w/freq: 10 min
QServerSocket: failed to bind or listen to the socket
2007-11-13 19:42:08.323 Failed to bind port 6543. Exiting.
joshua@masterbackend:~$ 

Any ideas of whats going on?

---

### Post by superm1 on 2007-11-13
> **kingjos said:**
> ok so i figured out my  first problem with installing my frontend system but now i'm having problems starting my backend.  so the output i get when trying to start my backend server is this:

joshua@masterbackend:~$ sudo mythbackend
2007-11-13 19:42:07.914 Using runtime prefix = /usr
2007-11-13 19:42:07.927 New DB connection, total: 1
2007-11-13 19:42:07.932 Connected to database 'mythconverg' at host: localhost
2007-11-13 19:42:07.934 Current Schema Version: 1160
Starting up as the master server.
2007-11-13 19:42:07.965 New DB connection, total: 2
2007-11-13 19:42:07.965 Connected to database 'mythconverg' at host: localhost
2007-11-13 19:42:07.967 EITHelper: localtime offset -6:00:00 
2007-11-13 19:42:07.969 New DB connection, total: 3
2007-11-13 19:42:07.970 Connected to database 'mythconverg' at host: localhost
2007-11-13 19:42:08.145 EITHelper: localtime offset -6:00:00 
2007-11-13 19:42:08.314 New DB scheduler connection
2007-11-13 19:42:08.314 Connected to database 'mythconverg' at host: localhost
QServerSocket: failed to bind or listen to the socket
2007-11-13 19:42:08.320 MediaServer::HttpServer Create Error
2007-11-13 19:42:08.320 Main::Registering HttpStatus Extension
2007-11-13 19:42:08.321 mythbackend version: 0.20.20070821-1 [www.mythtv.org]("http://www.mythtv.org")
2007-11-13 19:42:08.321 Enabled verbose msgs:  important general
2007-11-13 19:42:08.322 AutoExpire: Found 2 recorders w/max rate of 144 MiB/min
2007-11-13 19:42:08.322 AutoExpire: Required Free Space: 3.1 GB w/freq: 10 min
QServerSocket: failed to bind or listen to the socket
2007-11-13 19:42:08.323 Failed to bind port 6543. Exiting.
joshua@masterbackend:~$ 

Any ideas of whats going on?

Yeah.  You are starting your backend wrong.

```
sudo /etc/init.d/mythtv-backend restart
```

is the way to do it.


If the process is not running after that, check /var/log/mythtv/mythbackend.log

---

### Post by superm1 on 2007-11-14
> **kingjos said:**
> ok so i figured out my  first problem with installing my frontend system
Btw, what was the problem?  Odds are if you were getting a problem like this, other people will too.  We can add a check to work around whatever the selection causing the error was.

---

### Post by kingjos on 2007-11-14
Well I have know idea what the problem was but I did end up getting it to install on my frontend machine.  What I did different to get it to install was instead of doing the advanced installation and only installing the frontend I just chose the automatic installation and let the installer install everything onto my system.

Now that I have my frontend up and running I’m trying to get it to connect to my backend but am having no luck with so far.  I configured the ip address and host fields correctly when going through the general configuration wizard on the backend so I know its not that.  I also made the needed configurations to the MYSQL server so that other machines on the network could access the database as well.  I'm thinking the only other problem I could be having is that the username and/or password my frontend is using to connect to the database might not be what the database has.  So if someone knows how to access the database and figure out what usernames and passwords have been added to the database that would help me out a ton?

Thanks for all your help so far..

---

### Post by zelonewolf on 2007-11-16
I am also getting this exact same error message!

My setup:

Frontend-only mythbuntu
Soyo KT400 with AMD processor
768M ram
NVidia GeForce4 440MX
StreamZap remote control
Generic Creative labs PCI sound card (pre-Live!)

1 60g and 2 160g hard drives (IDE)

The hard drives are plugged into the onboard IDE RAID controller (could that be the problem?)  Just like the parent poster, the only way I was able to get it to work was to do the standard installation...frontend only just didn't work.

In anycase, no matter what combination of options I've tried, I ALWAYS get this error message.

> **kingjos said:**
> This is the  error message that I get.

any help would great !

We're sorry; the installer crashed. Please file a new bug report at [https://launchpad.net/ubuntu/+source/ubiquity/+filebug](https://launchpad.net/ubuntu/+source/ubiquity/+filebug) (do not attach your details to any existing bug) and a developer will attend to the problem as soon as possible. To help the developers understand what went wrong, include the following detail in your bug report, and attach the files /var/log/syslog and /var/log/partman:

Traceback (most recent call last):
  File "/usr/lib/ubiquity/bin/ubiquity", line 212, in <module>
    main()
  File "/usr/lib/ubiquity/bin/ubiquity", line 207, in main
    install(args[0])
  File "/usr/lib/ubiquity/bin/ubiquity", line 65, in install
    ret = wizard.run()
  File "/usr/lib/ubiquity/ubiquity/frontend/mythbuntu_ui.py", line 252, in run
    self.progress_loop()
  File "/usr/lib/ubiquity/ubiquity/frontend/mythbuntu_ui.py", line 330, in progress_loop
    (ret, realtb))
RuntimeError: Install failed with exit code 1
Traceback (most recent call last):
  File "/usr/share/ubiquity/mythbuntu_install.py", line 288, in <module>
    install.run()
  File "/usr/share/ubiquity/mythbuntu_install.py", line 100, in run
    self.configure_mythbuntu()
  File "/usr/share/ubiquity/mythbuntu_install.py", line 179, in configure_mythbuntu
    raise InstallStepError("MythbuntuApply Debconf Xfer failed with code %d" % ret)
InstallStepError: MythbuntuApply Debconf Xfer failed with code 255

---

### Post by superm1 on 2007-11-16
> **zelonewolf said:**
> I am also getting this exact same error message!

My setup:

Frontend-only mythbuntu
Soyo KT400 with AMD processor
768M ram
NVidia GeForce4 440MX
StreamZap remote control
Generic Creative labs PCI sound card (pre-Live!)

1 60g and 2 160g hard drives (IDE)

The hard drives are plugged into the onboard IDE RAID controller (could that be the problem?)  Just like the parent poster, the only way I was able to get it to work was to do the standard installation...frontend only just didn't work.

In anycase, no matter what combination of options I've tried, I ALWAYS get this error message.
I *just* performed a frontend installation inside a virtual machine myself.

Absolutely no issues.  During installation, the only changed options that I chose were "Advanced Install" and I filled out the username and password and server and database during the mythtv information page.

Anyone who is encountering this: what are the **exact** steps you are choosing, and please post your /var/log/syslog log.

---

