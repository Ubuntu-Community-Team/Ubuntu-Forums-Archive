---
title: "How to downgrade .22 to .21 on Karmic"
date: 2009-10-24
forum: Mythbuntu
---

### Post by lingenfr on 2009-10-24
Due to some driver incompatibilities, etc I have upgraded two of my laptops to Karmic (9.10). Unfortunately, it comes with mythtv-frontend .22 which is incompatible with my .21 backend. Several of my frontends are xbox/xbmc/xbmcmythtv which have not been updated yet, so I don't want to upgrade my backend until they are. So, I am looking for the best way to downgrade mythtv-frontend to .21 without hosing my laptops. Thanks.

---

### Post by azmyth on 2009-10-24
May look at the avenard repo.

[http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html](http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html)

Other than that, you may have to compile.

---

### Post by lingenfr on 2009-10-24
Not a good idea. I added his repositories and tried to force version and ended up with broken packages that took a bit to unscrew. Thanks for trying though.

---

### Post by dakota34 on 2009-10-25
I was able to grab the .21 debs from the [jaunty packages]("http://packages.ubunut.com/jaunty/graphics/")and isntall on a clean install of karmic without issue -- gdebi will give you an error messages listing the additional packages it needs, which you can grab from the same site -- so you may be be able to simply remove the .22 myth frontend and install the the 21 debs... then you should use the 'lock version' feature in Synaptic to prevent further upgrades - be careful not do do partial upgrades as they will, it looks like, upgrade even the locked versions ...

---

### Post by lingenfr on 2009-11-01
Thanks. Your solution tided me over. I upgraded to Karmic on all of my boxes today. My xbox was the one I was holding on. Still have to test it, but someone is working on the .22 protocol so hopefully it will work. The upgrade was painful.

---

### Post by muddysmind on 2009-11-02
> **dakota34 said:**
> I was able to grab the .21 debs from the [jaunty packages]("http://packages.ubunut.com/jaunty/graphics/")and isntall on a clean install of karmic without issue -- gdebi will give you an error messages listing the additional packages it needs, which you can grab from the same site -- so you may be be able to simply remove the .22 myth frontend and install the the 21 debs... then you should use the 'lock version' feature in Synaptic to prevent further upgrades - be careful not do do partial upgrades as they will, it looks like, upgrade even the locked versions ...

how did you install it?

got it, gdebi-gtk and grabbed the .deb files from [https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

---

### Post by psmbfuer on 2009-11-06
I ran into the same problem. Thanks to the input above, it was fairly straight forward. So hopefully this helps saves others a bit of time.

I have a separate backend and only needed to downgrade the frontend, so I went into Synaptic on the frontend and removed all of the &#8220;mythtv&#8221; packages. Be careful and note that I only did &#8220;Mark for Removal&#8221; not &#8220;Mark for Complete Removal&#8221; as I believe this would have also removed various configuration files that would have necessitated me entirely reconfiguring the frontend after installation. If someone can refute or confirm this, please do. So you can check, here are the files that were then removed.[INDENT][LIST]
[*]libmyth-0.22-0 will be removed

[*]libmyth-python will be removed

[*]mythbuntu-common will be removed

[*]mythbuntu-control-centre will be removed

[*]mythbuntu-log-grabber will be removed

[*]mythmovies will be removed

[*]mythtv-common will be removedlibmyth-0.22-0 will be removed

[*]libmyth-python will be removed

[*]mythbuntu-common will be removed

[*]mythbuntu-control-centre will be removed

[*]mythbuntu-log-grabber will be removed

[*]mythmovies will be removed

[*]mythtv-common will be removed

[*]mythtv-frontend will be removed

[*]mythtv-theme-iulius-osd will be removed

[*]mythtv-theme-mythbuntu will be removed

[*]mythtv-theme-retro-osd will be removed

[*]mythtv-theme-titivillus-osd will be removed

[*]mythvideo will be removed

[*]mythweather will be removed

[*]mythtv-frontend will be removed

[*]mythtv-theme-iulius-osd will be removed

[*]mythtv-theme-mythbuntu will be removed

[*]mythtv-theme-retro-osd will be removed

[*]mythtv-theme-titivillus-osd will be removed

[*]mythvideo will be removed

[*]mythweather will be removed
[/LIST][LIST]
[/LIST][/INDENT]
The packages that are needed include the following. These packages are for 32 bit x386 and although some are the same for 64 bit, not all are, if memory serves. You also need to add these pachages in the following order due to dependencies:

[INDENT][LIST=1]
[*]libraw1394-8_1.3.0-4ubuntu1_i386.deb
[*]libmyth-0.21-0_0.21.0+fixes19961-0ubuntu8_i386.deb
[*]mythtv-common_0.21.0+fixes19961-0ubuntu8_all.deb
[*]mythtv-frontend_0.21.0+fixes19961-0ubuntu8_i386.deb
[/LIST][/INDENT]

I then started myth-frontend and most of the old configuration was still there and it started up and started streaming TV and recordings from the backend, although with the default theme.

---

### Post by dscheste on 2009-11-11
> **psmbfuer said:**
> I ran into the same problem. Thanks to the input above, it was fairly straight forward. So hopefully this helps saves others a bit of time.
...........

[INDENT][LIST=1]
[*]libraw1394-8_1.3.0-4ubuntu1_i386.deb
[*]libmyth-0.21-0_0.21.0+fixes19961-0ubuntu8_i386.deb
[*]mythtv-common_0.21.0+fixes19961-0ubuntu8_all.deb
[*]mythtv-frontend_0.21.0+fixes19961-0ubuntu8_i386.deb
[/LIST][/INDENT]

I then started myth-frontend and most of the old configuration was still there and it started up and started streaming TV and recordings from the backend, although with the default theme.

Thank you psmbfuer, it worked.

---

