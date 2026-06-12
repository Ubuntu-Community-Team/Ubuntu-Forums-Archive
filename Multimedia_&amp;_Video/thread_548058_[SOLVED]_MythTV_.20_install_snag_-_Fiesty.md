---
title: "[SOLVED] MythTV .20 install snag - Fiesty"
date: 2007-09-10
forum: Multimedia &amp; Video
---

### Post by mkramer on 2007-09-10
I am trying to install the master backend server according to this very nice guide [https://help.ubuntu.com/community/MythTV_Feisty_Backend](https://help.ubuntu.com/community/MythTV_Feisty_Backend). 

I am just past the MySQL installation and on to the actual setup.  The backend server was already a LAMP server, thus MySQL was preinstalled, however I haven't missed the instruction on configuring the database with the correct root password.  Indeed it appears to be connecting.  The snag comes when I run mythtv-setup.  First of all, when I run it, I do get the graphical X-window asking me 
 if it's ok to close Mythbackend.  (X server = working correctly).  When I hit ok, the terminal buffer receives this output:
```

mason@dark-genius:~$ mythtv-setup
Stopping MythTV server: mythbackend No /usr/bin/mythbackend found running; none killed.
.
Xlib:  extension "XInputExtension" missing on display "localhost:10.0".
Failed to get list of devices
2007-09-10 20:38:44.420 Using runtime prefix = /usr
2007-09-10 20:38:44.448 DPMS is not supported.
2007-09-10 20:38:44.466 New DB connection, total: 1
2007-09-10 20:38:44.475 Connected to database 'mythconverg' at host: localhost
2007-09-10 20:38:44.476 Total desktop dim: 2560x1600, with 1 screen[s].
2007-09-10 20:38:44.485 Using screen 0, 2560x1578 at 0,22
2007-09-10 20:38:44.539 Current Schema Version: 1160
/usr/bin/mythtv-setup: line 38:  6279 Segmentation fault      (core dumped) /usr/bin/mythtv-setup.real "$@"


```
Then a graphical window asks if I want to run mythfilldatabase.  "OK" gets me a new terminal window, and this is what it reads:

```
2007-09-10 20:35:46.025 Using runtime prefix = /usr
2007-09-10 20:35:46.033 New DB connection, total: 1
2007-09-10 20:35:46.037 Connected to database 'mythconverg' at host: localhost
2007-09-10 20:35:46.039 There are no channel sources defined, did you run the setup program?

```
This window remains open for about two seconds, then closes.  Then the original terminal prints ```
Restarting MythTV server: mythbackend No /usr/bin/mythbackend found running; none killed.

``` and exits to a shell prompt.  I am finding this output to be rather cryptic, so if anyone can explain it to me, I'd appreciate it.  Particularly that last bit: no channel sources, did I run the setup program?  Seems rather chicken-and-egg to me.  And if this has been covered, I am sorry: my search didn't turn up much.

Edit: and it says there is a seg fault, does this indicate a permissions problem somewhere?

---

### Post by mkramer on 2007-09-10
Found my problem: [http://ubuntuforums.org/showthread.php?t=471502&highlight=mythtv+seg+fault](http://ubuntuforums.org/showthread.php?t=471502&highlight=mythtv+seg+fault)

OP says it is related to his X server.  I am using the Mac OS X server.  According to Mac documentation, " #
OpenGL : XInputExtension is not yet implemented. Maya and some GLUT applications require this extension.
#"

Apparently it's a mac problem.  I'll use a different computer to configure it.  Sorry to take up your time.

---

