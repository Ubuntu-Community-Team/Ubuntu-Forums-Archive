---
title: "Where can I get Jaunty mythTV packages for Karmic"
date: 2011-01-12
forum: Mythbuntu
---

### Post by gunnartr on 2011-01-12
I want to install MythTV 0.21 frontend on my Karmic, but the jaunty repositories seems to be gone. Where can I get the packages?

---

### Post by tgm4883 on 2011-01-12
You can get 0.21 packages for karmic at [https://launchpad.net/~mythbuntu/+archive/fixes-0.21/+packages](https://launchpad.net/~mythbuntu/+archive/fixes-0.21/+packages)

---

### Post by gunnartr on 2011-01-13
I was going to install my frontend acc. to this thread.: [http://ubuntuforums.org/showthread.php?t=1311270](http://ubuntuforums.org/showthread.php?t=1311270).

I copied following files.:
  libmyth-0.21-0_0.21.0+fixes21768-0ubuntu0+mythbuntu3_amd64,
 libmyth-0.21-0_0.21.0+fixes21768-0ubuntu0+mythbuntu3_lpia,
 libmyth-dev_0.21.0+fixes21768-0ubuntu0+mythbuntu3_amd64,
 libmyth-perl_0.21.0+fixes21768-0ubuntu0+mythbuntu3_all,
 libmyth-python_0.21.0+fixes21768-0ubuntu0+mythbuntu3_all,
 mythtv_0.21.0+fixes21768-0ubuntu0+mythbuntu3_all,
 mythtv-common_0.21.0+fixes21768-0ubuntu0+mythbuntu3_all,
 mythtv-frontend_0.21.0+fixes21768-0ubuntu0+mythbuntu3_amd64,
mythtv-transcode-utils_0.21.0+fixes21768-0ubuntu0+mythbuntu3_amd64,
mythtv-transcode-utils_0.21.0+fixes21768-0ubuntu0+mythbuntu3_i386

and Then launched Terminal, cd to the directory where I downloaded the packages and enter the following command:

sudo dpkg -i *debThere is something missing as the frontend wont start, can you help me on that?

---

### Post by tgm4883 on 2011-01-13
> **gunnartr said:**
> I was going to install my frontend acc. to this thread.: [http://ubuntuforums.org/showthread.php?t=1311270](http://ubuntuforums.org/showthread.php?t=1311270).

I copied following files.:
  libmyth-0.21-0_0.21.0+fixes21768-0ubuntu0+mythbuntu3_amd64,
 libmyth-0.21-0_0.21.0+fixes21768-0ubuntu0+mythbuntu3_lpia,
 libmyth-dev_0.21.0+fixes21768-0ubuntu0+mythbuntu3_amd64,
 libmyth-perl_0.21.0+fixes21768-0ubuntu0+mythbuntu3_all,
 libmyth-python_0.21.0+fixes21768-0ubuntu0+mythbuntu3_all,
 mythtv_0.21.0+fixes21768-0ubuntu0+mythbuntu3_all,
 mythtv-common_0.21.0+fixes21768-0ubuntu0+mythbuntu3_all,
 mythtv-frontend_0.21.0+fixes21768-0ubuntu0+mythbuntu3_amd64,
mythtv-transcode-utils_0.21.0+fixes21768-0ubuntu0+mythbuntu3_amd64,
mythtv-transcode-utils_0.21.0+fixes21768-0ubuntu0+mythbuntu3_i386

and Then launched Terminal, cd to the directory where I downloaded the packages and enter the following command:

sudo dpkg -i *debThere is something missing as the frontend wont start, can you help me on that?

No, sorry, don't do that.

Add this to your /etc/apt/sources.list then install/upgrade mythtv as normal. (using apt-get or synaptic)
```
deb http://ppa.launchpad.net/mythbuntu/fixes-0.21/ubuntu karmic main 
deb-src http://ppa.launchpad.net/mythbuntu/fixes-0.21/ubuntu karmic main
```

---

