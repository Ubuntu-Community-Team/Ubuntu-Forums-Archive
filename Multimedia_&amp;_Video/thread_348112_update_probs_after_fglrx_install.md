---
title: "update probs after fglrx install"
date: 2007-01-28
forum: Multimedia &amp; Video
---

### Post by Doug11 on 2007-01-28
I just installed the update for my radeon express,,everything went good as you can see here>>

doug@home:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series Generic
OpenGL version string: 2.0.6286 (8.33.6)

After rebooting, my update manager popped up saying there were updates available, so when I went to get updates, it errored out saying it couldn't update and gave me a command to use to fix the problem. Which is >>>sudo apt-get install -f
 Well, after I run the command, it stopped at one of those y/n questions if I wanted to contiunue. I said no and aborted because if I would have continued, it would have removed my fxlrx driver that I just installed. Here is the output it gave me>>

doug@home:~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  xorg-driver-fglrx-dev
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  xorg-driver-fglrx-dev
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 651kB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.


Anyone have any suggestions as to what I should do?

---

