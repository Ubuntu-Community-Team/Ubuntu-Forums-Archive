---
title: "Boxee install issue in Karmic"
date: 2009-11-08
forum: Multimedia Software
---

### Post by Fife3951 on 2009-11-08
Some trouble installing Boxee in Karmic Koala (32 bit).

After adding the Jaunty PPA (which I've been told works)...
```
dan@wehrmacht:~$ sudo apt-get install boxee
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  boxee: Depends: libkrb53 but it is not installable
E: Broken packages
dan@wehrmacht:~$ 
```

Any help would be much appreciated.

---

### Post by Beacon11 on 2009-11-08
Easy fix, check out the following URL: [http://forum.boxee.tv/showthread.php?p=60489](http://forum.boxee.tv/showthread.php?p=60489)

EDIT: I would really appreciate some feedback toward how well it works; I'm considering installing it myself on Karmic.

---

### Post by Fife3951 on 2009-11-08
WORKS!  

Thanks.

---

### Post by Fife3951 on 2009-11-08
> **Beacon11 said:**
> 

EDIT: I would really appreciate some feedback toward how well it works; I'm considering installing it myself on Karmic.

Works really well.  I'm planning on making my old(er) laptop in a permanent HTPC, and it should work perfectly well.  I find Boxee a little easier to use than XBMC, and I like all the Apps that are readily available.

My username on boxee is fife3951 as well... Boxee has a Twitter-esque friend system to see what your 'friends' are watching/sharing as well.

Now, if only it could stream content too...

---

### Post by sdowney717 on 2009-11-29
I got it working in karmic.
but there is one problem i have, the window suddenly vanishes and the sound keeps playing. it has happpened 3 times today and i only installed it today.

the sound plays until the show is over or you reboot.

i used this to set it up
[http://forum.boxee.tv/showthread.php?t=11589](http://forum.boxee.tv/showthread.php?t=11589)
repo is this
deb [http://apt.boxee.tv](http://apt.boxee.tv) jaunty main

---

