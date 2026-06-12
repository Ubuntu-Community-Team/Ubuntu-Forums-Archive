---
title: "[SOLVED] VLC/VLC-nox install problem with intrepid"
date: 2008-10-30
forum: Multimedia Software
---

### Post by pognonec on 2008-10-30
I did screw up here:
I had a problem with VLC (inverted colors: skin of white people looked blue!), so I wanted to reinstall it manually... I got several warnings, telling me that some dependancies were missing. I tried to install them manually. But everything got weird. Here is what I get when trying to reinstall VLC:

```
philippe@philippe:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vlc: Depends: libavcodec1d (>= 0.cvs20070307) but it is not installable
       Depends: libavformat1d (>= 0.cvs20070307) but it is not installable
       Depends: libavutil1d (>= 0.cvs20070307) but it is not installable
       Depends: vlc-nox (= 0.9.5+x264snapshot20080928+faad2.6.1-1~ppa1) but 0.9.4-1ubuntu3 is to be installed
E: Broken packages
philippe@philippe:~$ sudo apt-get install vlc-nox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vlc-nox: Depends: libavutil1d (>= 0.cvs20070307) but it is not installable
           Depends: libgnutls13 (>= 2.0.4-0) but it is not installable
           Depends: libpostproc1d (>= 0.cvs20070307) but it is not installable
           Depends: libswscale1d (>= 0.cvs20070307) but it is not installable
E: Broken packages
philippe@philippe:~$ 
```

Synaptic does not allow me to reinstall VLC, and does not show VLC-nox... How can I get VLC reinstalled??

Here is what Synaptic says when trying to reinstall VLC:

vlc:
 Depends: libavcodec1d (>=0.cvs20070307) but it is not installable
 Depends: libavformat1d (>=0.cvs20070307) but it is not installable
 Depends: libavutil1d (>=0.cvs20070307) but it is not installable
  Depends: vlc-nox (=0.9.5+x264snapshot20080928+faad2.6.1-1~ppa1) but 0.9.4-1ubuntu3 is to be installed

---

### Post by mc4man on 2008-10-30
You may want to wait awhile - maybe the intrepid repo's are maxed out. 

What looks strange is you seem to be trying to install the korn ppa version which I thought was only for hardy. In any event you may be happier with the intrepid ver. (1 window for player and video)

I'd go to System -> Administration -> Software sources and under 'ubuntu software' tab make sure first 4 boxes are checked, and under 'third party software' disable korn ppa if there.

After that open synaptic and if it says 'broken package(s)' then let it repair. (edit -> 'fix broken packages' after it's done click apply and then try installing vlc again

---

### Post by pognonec on 2008-10-30
After fighting with individual package manual install, I come down (in synaptic, when trying to install vlc) to:

vlc:
  Depends: vlc-nox (=0.9.5+x264snapshot20080928+faad2.6.1-1~ppa1) but 0.9.4-1ubuntu3 is to be installed

But that one, I cannot fix...

Any idea?

---

### Post by pognonec on 2008-10-30
> **mc4man said:**
> 
I'd go to System -> Administration -> Software sources and under 'ubuntu software' tab make sure first 4 boxes are checked, and under 'third party software' disable korn ppa if there.


That did it!

MERCI! Thank you!!

---

### Post by omer.arslan on 2009-04-14
thank you, it worked for me. i couldn't install vlc because of an incompleted grapichs driver installation.

---

