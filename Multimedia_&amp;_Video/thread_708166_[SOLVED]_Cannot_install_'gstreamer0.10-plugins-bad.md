---
title: "[SOLVED] Cannot install 'gstreamer0.10-plugins-bad-multiverse'"
date: 2008-02-26
forum: Multimedia &amp; Video
---

### Post by mahinda on 2008-02-26
I need to install  'gstreamer0.10-plugins-bad-multiverse' to run movie file, this message came in half way, 

This application conflicts with other installed software. To install 'gstreamer0.10-plugins-bad-multiverse' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.

I open synaptic package manager, but don't know what to do. Please help me. Remember, I am new to ubuntu and linux.

---

### Post by Bubba64 on 2008-02-26
Here is a post for everything you need.
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
Here is another I just noticed that is alittle simpler and seems to answer your question.
[http://ubuntuforums.org/showthread.php?t=708077](http://ubuntuforums.org/showthread.php?t=708077)

---

### Post by mahinda on 2008-02-26
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

this has lot of information and I did some, but I don't know which one in relevant to me


[http://ubuntuforums.org/showthread.php?t=708077](http://ubuntuforums.org/showthread.php?t=708077)
this one I did, I add whole Medibuntu repository.  I got errors when I add i386, amd64, ppc

But still same error appear.  Anything else I can do???

---

### Post by mahinda on 2008-02-26
when I try with synaptic package manager
This message came

gstreamer0.10-plugins-bad-multiverse:
 Depends: libmjpegtools0c2a but it is not going to be installed


then I found libmjpegtools0c2a  in the web and try to install manually, then I got this errror

 Dependency is not satisfiable: libquicktime0



what shall I do now? :confused::confused:

---

### Post by PmDematagoda on 2008-02-26
Please post the output of:-
```
cat /etc/apt/sources.list
```

---

### Post by mahinda on 2008-02-26
thanks.
The problem solved. I manually installed several program from here
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)  probable, I did it long way, how ever now it working.

thanks again

---

