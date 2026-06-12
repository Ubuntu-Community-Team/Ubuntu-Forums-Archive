---
title: "ALSA professionals required!"
date: 2007-02-02
forum: Multimedia &amp; Video
---

### Post by hyby on 2007-02-02
My apologies for the double post, but im in a little strife with my sound (well actually for the whole year). 

I think i am close to solving my problem, however i have hit a roadblock. I was wondering if i could get some assistance.

I have recompiled my ALSA-modules that are supposed to solve my problems with various guides. However, when it comes to running the .deb file i have an error:

davinci@davinci:~$ sudo dpkg -i alsa-modules-2.6.17-10-386_1.0.14rc1-0ubuntu1_i386.deb
(Reading database ... 91539 files and directories currently installed.)
Preparing to replace alsa-modules-2.6.17-10-386 1.0.14rc1-0ubuntu1 (using alsa-modules-2.6.17-10-386_1.0.14rc1-0ubuntu1_i386.deb) ...
Unpacking replacement alsa-modules-2.6.17-10-386 ...
Setting up alsa-modules-2.6.17-10-386 (1.0.14rc1-0ubuntu1) ...
FATAL: Could not open '/boot/System.map-2.6.17-10-386': No such file or directory

However, when i search the /boot/ folder i find that the file it requires is /boot/system.map-2.6.17-10-generic.

Now, i was wondering is there a way i can rename this folder? or do i have go through the deb. file and find the line where i have to change so that i targets the xxx-generic folder rather than the xxx-i386 folder??

---

