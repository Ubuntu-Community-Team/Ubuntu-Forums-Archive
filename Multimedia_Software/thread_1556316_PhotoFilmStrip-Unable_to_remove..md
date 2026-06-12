---
title: "PhotoFilmStrip-Unable to remove."
date: 2010-08-19
forum: Multimedia Software
---

### Post by svenkatesan on 2010-08-19
Hi
I have a problem with my ubuntu 10.04.All updates installed.
I downloaded a software called "[Photofilmstrip]("http://www.photofilmstrip.org/4-0-Download.html")" -debian based from their website and installed by Package Manager,at the end it throwed some error messeage,then I cancel the installation but the software become visible in Application---->sound and video.I can use that program to some extend but I see an alert (see the pic attached)
I click that update-Manager and gone for partial update due to unstability of that package but finally it can't remove the package.
Can somebody guide me to remove the whole package?
I tried in add/remove -its not visible there.
I tried these too
[PHP]sudo dpkg --remove --force-remove-reinstreq photofilmstrip
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 273445 files and directories currently installed.)
Removing photofilmstrip ...
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f]

update-python-modules: error: /usr/share/python-support/photofilmstrip.private is not a directory
dpkg: error processing photofilmstrip (--remove):
 subprocess pre-removal script returned error exit status 2
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f]

update-python-modules: error: /usr/share/python-support/photofilmstrip.private is not a directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 photofilmstrip

[/PHP]
Thanks in advance.

---

### Post by svenkatesan on 2010-08-22
I got this out error messeage by using this method given below site.
[http://www.khattam.info/solved-subprocess-pre-removal-script-returned-error-exit-status-2-error-2009-08-04.html#comment-834](http://www.khattam.info/solved-subprocess-pre-removal-script-returned-error-exit-status-2-error-2009-08-04.html#comment-834)

---

### Post by hammerwerfer on 2011-01-29
Hi, i dont know if u got this problem solved. But i found a solution here:

[http://forum.ubuntuusers.de/topic/photofilmstrip-installiert-synapitc-funkionie/?highlight=paketverwaltung#post-2584798](http://forum.ubuntuusers.de/topic/photofilmstrip-installiert-synapitc-funkionie/?highlight=paketverwaltung#post-2584798)

```

sudo rm /usr/share/python-support/photofilmstrip.private
sudo mkdir /usr/share/python-support/photofilmstrip.private
sudo dpkg --force-all -r photofilmstrip

```

---

