---
title: "Google Earth Will not Uninstall"
date: 2008-06-30
forum: Multimedia Software
---

### Post by dbsoundman on 2008-06-30
I had a perfectly operational installation of Google Earth 4.3 up until earlier this evening. For some reason, some library got deleted and it wouldn't run, so I decided to try to remove it. However, I couldn't get it to uninstall; there is no uninstaller either. So, I decided to install through medibuntu/synaptic and see if it would overwrite the old installation. No dice, it just created a second one. So I got rid of that one, but I still have the old one. To make matters worse, the "new" installation crashed on me. So how can I fix all this and get google earth going again? I'm on Hardy Heron.

Thanks,
Dan

---

### Post by dbsoundman on 2008-06-30
Here's a new development: I tried running the google .bin from the site again, and this is what I got:
```
dan@blackdiamond:~/Desktop$ sudo sh GoogleEarthLinux.bin 
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.3.7204.836..............................................................
setup.data/bin/Linux/amd64/setup.gtk2: error while loading shared libraries: libxml2.so.2: cannot open shared object file: No such file or directory
setup.data/bin/Linux/amd64/setup.gtk: error while loading shared libraries: libSM.so.6: cannot open shared object file: No such file or directory
The setup program seems to have failed on amd64

Fatal error, installer failed to run at all!

```

This is a bad thing. What happened?

-Dan

---

### Post by etlpkby on 2009-01-12
Moved my post to here:-

[http://ubuntuforums.org/showthread.php?p=6539564#post6539564]("http://ubuntuforums.org/showthread.php?p=6539564#post6539564")

..as it was regarding INSTALL of googleearth and this topic is UNINSTALL :P

---

### Post by binbash on 2009-01-12
add medibuntu to your repos and install it via apt-get

---

### Post by goosem on 2009-08-22
I installed Google Earth to Ubuntu Hardy Heron via Medibuntu following the published instructions. The initial problem was that the GE display flickers and I have not been able to find a solution. My second problem, having decided to uninstall GE, is that in spite of following published instructions to uninstall, it still appears in Applications-Internet-Google Earth and will launch (however still flickering). Any further attempts to uninstall result in a message that it is not installed! Also it does not appear in Add/Remove. Can anyone please advise what I might have done wrong and how I might resolve the problem.

---

