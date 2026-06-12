---
title: "HOWTO: Fix choppy flash videos on Intel 945GM"
date: 2009-07-11
forum: Multimedia Software
---

### Post by happyponcho42 on 2009-07-11
Reference: [http://ubuntuforums.org/showthread.php?t=1208339](http://ubuntuforums.org/showthread.php?t=1208339)

Cliffnotes: Some people with Intel 945GM may notice that within the LiveDVD environment of Sabayon 4.2, you can play full screen HD flash videos (hulu in particular) without a hitch, a feat that not many distros can pull off in a LiveCD environment, let alone an installed version.  This might also apply to Ubuntu's LiveDVD since Ubuntu tends to have very good hardware support and the community is great.  Anyways, I found it annoying that in the LiveDVD, I could do all that, but once I loaded up the installed version, flash was extremely choppy and unbearable to watch in fullscreen.  So...

I ran a diff on the entire filesystem of the LiveDVD and compared it to a local installation to figure out why the LiveDVD is able to play the fullscreen HD flash videos flawlessly, yet the local installations are unable to do the same.  I found the following:

> 
diff /mnt/oldroot/etc/csh.env /etc/csh.env
21a22
> setenv LIBGL_DRIVERS_PATH '/usr/lib64/dri:/usr/lib32/dri'


So...the solution is to edit your /etc/csh.cshrc file and add
```
setenv LIBGL_DRIVERS_PATH '/usr/lib64/dri:/usr/lib32/dri'
```
...then reboot and go ahead and test out some HD flash videos on hulu.

People with Intel 945GM's (perhaps this might apply to other Intel chipsets too), please try it out and report your results here.

---

### Post by prshah on 2009-07-11
> **happyponcho42 said:**
> So...the solution is to edit your /etc/csh.cshrc file and add
```
setenv LIBGL_DRIVERS_PATH '/usr/lib64/dri:/usr/lib32/dri'
```
...then reboot and go ahead and test out some HD flash videos on hulu.


Good research and solution.

One can also add/edit that LIBGL_DRIVERS_PATH to your /etc/environment```
LIBGL_DRIVERS_PATH="/usr/lib64/dri:/usr/lib32/dri"
```

---

