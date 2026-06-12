---
title: "remote shutdown question"
date: 2009-06-09
forum: Networking &amp; Wireless
---

### Post by devin0 on 2009-06-09
I have a ubuntu computer on the same network as three windows computers and would like to be able to shut them down remotely through the ubuntu computer. Is there a way of doing this?

---

### Post by linuxdanny on 2009-06-09
Hey, 
Need more info,
Did you want to use a 3rd party linux & windows compatible application
or
Did you want to find a way without any additional applications, If this is what your trying to do please list the windows OS versions ie xp or vista server ect

Cheers

---

### Post by lensman3 on 2009-06-09
Windows has a shutdown command that can be issued from a DOS window or command line.  You could add a user to windows called "shutdown" and all that user could was run a "shutdown -now" script.  Don't even add a password.  Once enter is hit the machine crashes.  

Sorry I don't know how to establish a connection from Linux to XP so that the shutdown user would take over.

On Linux just a user called shutdown that would run the program shutdown.  The line in /etc/passwd would look like:

shutdown:x:300:400:shutdown:/var/adm:/sbin/shutdown

This is untested, but I saw a line like this on an old SUN1 machine that had a user called sync.  This was for a user to sync the disks without having to login.  The last field is for a legal shell.  There is a file on the computer that list "legal" shell and shutdown would have to added to it.

You would have to test this to make sure there are no security holes, like stopping the shutdown process and gaining root access.

---

### Post by zadehas on 2009-06-10
Go to My Computer -> Properties, the Remote tab.
Check "Allow users to connect remotely to this computer".

In ubuntu, write this command:
rdesktop windows_ip

This will connect you to the Windows desktop.

Alternate:


install open ssh on windows and issue shutdown at the command prompt.

---

