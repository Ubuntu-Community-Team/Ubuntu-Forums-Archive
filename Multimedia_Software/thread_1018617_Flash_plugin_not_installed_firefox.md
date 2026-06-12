---
title: "Flash plugin not installed firefox"
date: 2008-12-22
forum: Multimedia Software
---

### Post by kulkarniniraj on 2008-12-22
hello
 today i havve set up ubutnu hardy. When i installed flash plugin (nonfree) (version 10.X) from synaptic neither it is shown in about:plugins page nor it plays any video. Instead it shows a message that flash player is of old version. How can i manually add that plugin ? I have searched /usr/lib directory in which i found flash library but still it is not working. Please help.

---

### Post by namdung on 2008-12-22
> **kulkarniniraj said:**
> hello
 today i havve set up ubutnu hardy. When i installed flash plugin (nonfree) (version 10.X) from synaptic neither it is shown in about:plugins page nor it plays any video. Instead it shows a message that flash player is of old version. How can i manually add that plugin ? I have searched /usr/lib directory in which i found flash library but still it is not working. Please help.

The flash plugin in Ubuntu repository is broken. Remove, download .deb file and install.

[http://ubuntuforums.org/showthread.php?t=1012893](http://ubuntuforums.org/showthread.php?t=1012893) 
[http://ubuntuforums.org/showthread.php?t=1013945](http://ubuntuforums.org/showthread.php?t=1013945)

---

### Post by wolfen69 on 2008-12-22
see my response [here]("http://ubuntuforums.org/showthread.php?t=1018291") (post #5) to get it working.

---

### Post by kulkarniniraj on 2008-12-23
I saw the problem in terminal which was missing libraries libnss3.so
I installed some libraries & its done.

---

