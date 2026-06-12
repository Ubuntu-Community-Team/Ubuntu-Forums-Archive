---
title: "Amarok won't launch"
date: 2009-05-06
forum: Multimedia Software
---

### Post by workenchina on 2009-05-06
I had this problem in 8.10 and thought maybe 9.04 would fix it.  I dual boot with Vista.

I have tried to load Amarok both from the GUI launcher and the terminal.  When I launch from GUI, I get the splash screen and nothing else.  After trying to open again I get a debugging message:

 p, li { white-space: pre-wrap; }  Unable to create a valid backtrace.
 
 This backtrace appears to be of no use.
 This is probably because your packages are built in a way which prevents creation of proper backtraces, or the stack frame was seriously corrupted in the crash.
 

When I launch from the terminal I get:

 p, li { white-space: pre-wrap; }  
trying to create local folder /home/workenchina/.kde/cache-workenchina-laptop: Permission denied
trying to create local folder /home/workenchina/.kde/cache-workenchina-laptop: Permission denied
trying to create local folder /home/workenchina/.kde/tmp-workenchina-laptop: Permission denied
trying to create local folder /home/workenchina/.kde/tmp-workenchina-laptop: Permission denied
trying to create local folder /home/workenchina/.kde/tmp-workenchina-laptop: Permission denied
trying to create local folder /home/workenchina/.kde/tmp-workenchina-laptop: Permission denied
trying to create local folder /home/workenchina/.kde/tmp-workenchina-laptop: Permission denied
trying to create local folder /home/workenchina/.kde/share: Permission denied
amarok(7448): Failed to lock file "/home/workenchina/.kde/cache-workenchina-laptop/kpc/kde-icon-cache.lock" , last result = 2 
amarok(7448): Couldn't create index file "/home/workenchina/.kde/cache-workenchina-laptop/kpc/kde-icon-cache.index" 
trying to create local folder /home/workenchina/.kde/share: Permission denied
[COLOR=Red]*above line x212*[/COLOR]
trying to create local folder /home/workenchina/.kde/cache-workenchina-laptop: Permission denied
trying to create local folder /home/workenchina/.kde/cache-workenchina-laptop: Permission denied
amarok(7448) KToolInvocation::klauncher: klauncher not running... launching kdeinit
trying to create local folder /home/workenchina/.kde/share: Permission denied
trying to create local folder /home/workenchina/.kde/tmp-workenchina-laptop: Permission denied
trying to create local folder /home/workenchina/.kde/tmp-workenchina-laptop: Permission denied
trying to create local folder /home/workenchina/.kde/tmp-workenchina-laptop: Permission denied
trying to create local folder /home/workenchina/.kde/tmp-workenchina-laptop: Permission denied
trying to create local folder /home/workenchina/.kde/tmp-workenchina-laptop: Permission denied
trying to create local folder /home/workenchina/.kde/tmp-workenchina-laptop: Permission denied
trying to create local folder /home/workenchina/.kde/tmp-workenchina-laptop: Permission denied
trying to create local folder /home/workenchina/.kde/share: Permission denied
trying to create local folder /home/workenchina/.kde/socket-workenchina-laptop: Permission denied
kdeinit4: Aborting. bind() failed: : Permission denied
Could not bind to socket '/home/workenchina/.kde/socket-workenchina-laptop/kdeinit4__0'


I tried $sudo chown -R workenchina.workenchina /home/workenchina/.kde/share but to no avail.  Any help would be appreciated

---

### Post by workenchina on 2009-05-13
Still having the same problems.  Can anyone answer the question or direct me to a thread that has an answer.  I have searched and searched, still nothing.  Thanks for your help.

---

