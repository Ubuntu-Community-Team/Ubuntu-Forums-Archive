---
title: "First time using Ardour.  Locked memory issue?"
date: 2011-05-30
forum: Multimedia Software
---

### Post by 0_irishboy_0 on 2011-05-30
Hey everyone!


I downloaded Ardour tonight because I'd like to begin recording some guitar tracks in the near future and I wanted to try to get familiar with it.  When I open Ardour, I get this message:

> WARNING: Your system has a limit for maximum amount of locked memory. This might cause Ardour to run out of memory before your system runs out of memory. 

You can view the memory limit with 'ulimit -l', and it is normally controlled by /etc/security/limits.confI tried running ```
sudo getit /etc/security/limits.conf
``` in a terminal and got a message saying: > "(gedit:8591): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.66SLWV': No such file or directory
The window that popped up said this:
```
#<domain>      <type>  <item>         <value>
#

#*               soft    core            0
#root            hard    core            100000
#*               hard    rss             10000
#@student        hard    nproc           20
#@faculty        soft    nproc           20
#@faculty        hard    nproc           50
#ftp             hard    nproc           0
#ftp             -       chroot          /ftp
#@student        -       maxlogins       4

# End of file
```No line for @audio that was mentioned in another thread.


Does anybody have an idea on exactly how I can "unlock"  the memory for Ardour?  It it matters, I'm running 11.04 32bit on an Asus g73jw laptop.

---

