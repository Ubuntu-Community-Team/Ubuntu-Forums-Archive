---
title: "How to install Gimp Stable instead of Unstable (unmet dependencies, held broken pack)"
date: 2016-09-05
forum: Multimedia Software
---

### Post by jesusguevarautomotriz on 2016-09-05
Hi,

Every time I tried to install Gimp in my Lubuntu 1.4.04.5 LTS, it installed a version 2.9 of Unstable repository [https://launchpad.net/~anton+/+archive/ubuntu/photo-video-apps](https://launchpad.net/~anton+/+archive/ubuntu/photo-video-apps).
I Remove That repository using Y PPA Manager and now when I try to install Gimp throws me the following error:

```

$ sudo apt install gimp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gimp : Depends: libgimp2.0 (<= 2.8.10-z) but 2.9.2.1024+git20160514.959f80d5-1pmo3~trusty is to be installed
        Depends: gimp-data (<= 2.8.10-z) but 2.9.2.1024+git20160514.959f80d5-1pmo3~trusty is to be installed
E: Unable to correct problems, you have held broken packages.



```

Ho I can solve this?, Thanks.

---

### Post by mc4man on 2016-09-05
```
I Remove That repository using Y PPA Manager and now...

gimp : Depends: libgimp2.0 (<= 2.8.10-z) but 2.9.2.1024+git20160514.959f80d5-1pmo3~trusty is to be installed
        Depends: gimp-data (<= 2.8.10-z) but 2.9.2.1024+git20160514.959f80d5-1pmo3~trusty is to be installed
```
Don't know what Y PPA does when removing so you could try purging both of the above,
```
sudo apt purge libgimp2.0 gimp-data
```
Then look & see if any ppa packages can be auto removed, if so,  do so.

Or it may be better to just add back the ppa & update your sources. Then  use ppa-purge on the ppa, afterwards  install gimp or update sources, then install gimp.

---

### Post by jesusguevarautomotriz on 2016-09-05
Solved! With Your Reply, Thanks.

---

### Post by mc4man on 2016-09-05
You may have some other ppa packages still installed, for the most part they look to be slightly newer versions. So if no issue you could leave.
Otherwise ppa-purge would work fine though one would need to first remove libmypaint  before running the ppa-purge command. (if gimp was installed

Edit: actually ppa-purge would have a problem with that ppa, likely due to how the ppa named. 
Can be left as is otherwise synaptic would be best way to revert all that *could* of been upgraded or installed from there.

---

### Post by Bucky Ball on 2016-09-06
Just out of curiousity, is Gimp not in the repositories in Lubuntu, i.e. Synaptic Package Manager? Just wondering what the problem was with that version, unless I'm missing something ... :-k I've never installed it from a PPA in eight years.

I'm on 16.04 with Gimp 2.8.16 from the repos. 

In any case, please help others by marking the thread as solved. See the last link in my signature at the bottom of this post. This will *_not_* close the thread. Thanks.

---

### Post by jesusguevarautomotriz on 2016-09-06
I think that the conflict occurred because when long had the recent installation, install Hotshots very comfortable app to make Screenshots from PPA before to install Gimp; But that PPA "Anton" points to an unstable version of Gimp.

Now I first installed Gimp Stable and after  installed Hotshots from ppa: ubuntuhandbook1/apps.

---

