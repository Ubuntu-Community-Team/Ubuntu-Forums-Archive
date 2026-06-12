---
title: "Error message in body for message"
date: 2006-10-01
forum: Multimedia &amp; Video
---

### Post by Fingerlakes_Dave on 2006-10-01
> **Fingerlakes_Dave said:**
> OK.  I downloaded the newest nvidia drivers.  I found the section
in help/faq on how to install.  Printed out.

 Tried to do exactly what is written.  I now cannot get the xserver to run.  All I get is a command line login and when I do login, it's at the commandline desktop.

 OK.

  Tried all the suggestions.  The only one that worked was sudo dpkg-reconfigure xserver-xorg, then startx

 tried above with -phigh. **No luck.**

 Tried to run sudo nvidia-glx-config enable. got md5 error. redid the ckecksum afet edit of nv to nvidia.  again ran dpkg-reconfigure xserver-xorg, then startx. **Zero luck**

tried all suggestion previouls posted except Envy.  Not sure if that would kill my system.

  Every try of the above comands gets me:

 API mismatch : the NVIDIA kernel module has the version 1.0-7174, but the X module has the version 1.0-8762. 
 Please make usre that the kernel module and all NVIDIA components have the same version.
(EE)  Failed to initialize the NVIDIA kernel module!
(EE)  Please ensure that there is a supported NVIDIA GPU in this system, (EE)  and that the NVIDIA device files have been created properly. 
(EE)   Please 
(EE)  consult the Readme for details
(EE)  *** Aborting ***
(EE)  Screens found, but none have a usable configuration.

 OK.

  I stand by my previous statements: linux is way too tough for you average user to learn.  Hell, most average users don't even know about driver updates unless something prompts them to do it.

  I'm still trying, yet I still am exhausted with this try, try again stuff.  :(  ](*,) 

Dave

---

### Post by TheFlamingBush on 2006-10-01
did you use automatix yet?

---

### Post by Fingerlakes_Dave on 2006-10-01
> **TheFlamingBush said:**
> did you use automatix yet?

 Tried. **Same result as my post: wrong kernel.**

---

### Post by Fingerlakes_Dave on 2006-10-02
OK.

  Now I'm really baffled.  

  I tried everything suggested I felt wouldn't kill my system.
I now have 1024x786 @ 85hz.

  Why am I not cheering?

  I haven't got a clue what worked!  Nada!

  It could have been any of a couple dozen commands, attempts at edits, reconfigures, etc.....:-? :-? :-? 

  I just pray they never send down an xorg.conf file in an update!

Dave

---

