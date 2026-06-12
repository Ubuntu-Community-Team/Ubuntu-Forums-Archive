---
title: "GLX nd nvidia-settings problems - installed wrong?"
date: 2007-03-07
forum: Multimedia &amp; Video
---

### Post by 94ranger on 2007-03-07
Community,

I have installed the drivers for my 7900GT using Envy, I am having several problems. Screen savers are very slow. When I run nvidia-settings from System Tools, I get "Failed to execute child process "/usr/bin/nvidia-setting" (No such file or directory)." And finally, 3ddesktop does not work either. I get: 

james@james-ubuntu:~$ 3ddesk --acquire
Attempting to start 3ddesktop server.
Daemon started.  Run 3ddesk to activate.
3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration.  Exiting.
Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddeskd)

Did I install this wrong? How can this be fixed? Help!

Thank you!

EDIT: I noticed in Synaptec that the nvidia-glx and nvidia-glx-dev packages are not installed. I was under the impression that Envy installed the correct driver and I do not need these. Please bear with me as this is all totally new to me. Should this packages be installed, and what effect will they have on the Envy driver installation? I would greatly appreciate a helping hand! Thank you!

---

### Post by igknighted on 2007-03-07
Envy doesn't install the drivers from the repo's, but rather from Nvidia's site, so nvidia-glx would not be installed if you used Envy.

If you downloaded and installed envy, you must then hit ctl-alt-F1 to drop to a shell (text only), and then type "sudo envy".  It should do everything then.  As long as no errors were seen it /should/ be good.

If you did all this, what are the results of the following commands in the terminal:
```
glxinfo | grep direct
cat /etc/X11/xorg.conf
```

---

### Post by 94ranger on 2007-03-07
igknighted,

Thanks for the help. I'm not at the machine rght now, so I'll try it when I get in tonight.

So Ency installed the drivers only, and not glx? And I want to make sure I understand something: EVen after I've run Envy, I can\safely go to the console and run sudo envy like you said without uninstalling what I did w/ the Ency wizard?

Thank you!

---

### Post by lanchongzi on 2007-03-13
hi guys
i just tried igknighted's tip with the result that my screnn went black halfway through... :(
sooooo, what do i do now????

---

