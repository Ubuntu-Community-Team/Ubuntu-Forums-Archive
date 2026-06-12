---
title: "Dependency Hell: VLC"
date: 2014-03-29
forum: Multimedia Software
---

### Post by Wbie on 2014-03-29
Sound inexplicably stopped during video file playback via VLC.  I removed via terminal, no problems.  I tried to reinstall and got:

> Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 vlc : Depends: vlc-nox (= 2.0.8-1) but it is not going to be installed
       Depends: libvlccore5 (>= 2.0.0) but it is not going to be installed
       Recommends: vlc-plugin-notify (= 2.0.8-1) but it is not going to be installed
       Recommends: vlc-plugin-pulse (= 2.0.8-1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


Attempting to install via software center gives:

>  The following packages have unmet dependencies:

vlc: Depends: vlc-nox (= 2.0.8-1) but 2.1.2-1~ppa1 is to be installed
     Depends: libavcodec-extra-53 (>= 6:0.8.7) but 6:0.8.10ubuntu0.13.10.1 is to be installed
     Depends: libavutil-extra-51 (>= 6:0.8.7) but 6:0.8.10ubuntu0.13.10.1 is to be installed
     Depends: libc6 (>= 2.15) but 2.17-93ubuntu4 is to be installed
     Depends: libfreetype6 (>= 2.2.1) but 2.4.12-0ubuntu1.1 is to be installed
     Depends: libgcc1 (>= 1:4.1.1) but 1:4.8.1-10ubuntu9 is to be installed
     Depends: libqtcore4 (>= 4:4.8.0) but 4:4.8.4+dfsg-0ubuntu18.1 is to be installed
     Depends: libqtgui4 (>= 4:4.7.0~beta1) but 4:4.8.4+dfsg-0ubuntu18.1 is to be installed
     Depends: libstdc++6 (>= 4.6) but 4.8.1-10ubuntu9 is to be installed
     Depends: zlib1g (>= 1:1.2.3.3) but 1:1.2.8.dfsg-1ubuntu1 is to be installed


Here are my dependencies: [https://app.box.com/s/7kr82y0rpr43mv6iiu1b](https://app.box.com/s/7kr82y0rpr43mv6iiu1b)

It's 13.10 w/ Unity Removed and Cinnamon installed.

Any help gratefully accepted and thanks in advance!

---

### Post by squakie on 2014-03-29
Do yourself a favor and install synaptic package manager:

sudo apt-get install synatpic

When that finishes:

sudo apt-get purge vlc

Now via the menus start up the synaptic package manger.  The password is just your normal password.

Enter vlc in the search string, click it and select mark for installation, then click Apply.

If you still get errors please post them back here.

---

### Post by su:bhatta on 2014-03-29
> **Wbie said:**
> 

Here are my dependencies: [https://app.box.com/s/7kr82y0rpr43mv6iiu1b](https://app.box.com/s/7kr82y0rpr43mv6iiu1b)



+1 to squakie, give that a try.

Also, that link you provided is list of your sources/repositories enabled, not dependencies.

See: [http://askubuntu.com/questions/292899/role-of-dependencies-while-installing-software](http://askubuntu.com/questions/292899/role-of-dependencies-while-installing-software)

---

### Post by mc4man on 2014-03-29
You were using a ppa version of vlc & no longer have the ppa enabled. so either - 
re-enable the ppa, update sources & re-install vlc
or
completely remove all vlc packages, update sources & install the saucy repo vlc

Usually this will remove all, otherwise ck. & do so in synaptic - 
```
sudo apt-get purge vlc-data
```

(there are usually 7 vlc packages installed - 
vlc-plugin-pulse
vlc-plugin-notify
vlc-nox
libvlc5
vlc
libvlccore7 
vlc-data

---

### Post by squakie on 2014-03-29
Missed the vlc-data portion - I thought purging vls itself would take care of that, since it's added when you install vlc, hence my above post to purge vlc - the rest is just as I already stated.  For the OP:  ALWAYS go through the repositories when possible (this is why I had you install synaptic).  Using tools like synaptic (another view of apt) with the normal repositories will install dependencies as needed.

---

### Post by Wbie on 2014-03-30
Thanks for all the help guys - the Synaptics route worked.

Also - yeah, my bad on the dependency/repository confusion; just typing too fast. :)

---

### Post by su:bhatta on 2014-03-31
So you got VLC working, good for you.

If the issue is resolved, please mark the thread as 'Solved' using the 'Thread Tools' on the top right of the page.

---

