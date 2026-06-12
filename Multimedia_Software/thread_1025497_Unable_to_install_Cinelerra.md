---
title: "Unable to install Cinelerra"
date: 2008-12-30
forum: Multimedia Software
---

### Post by penguintutor on 2008-12-30
I am trying to install Cinelerra on Ubuntu 8.10 Intrepid Ibex, but not having much success. 

I followed the instructions at: [http://cvs.cinelerra.org/getting_cinelerra.php]("http://cvs.cinelerra.org/getting_cinelerra.php"), but I get an error when trying to update, and Cinelerra is not available for install.

Synaptic sources lists as:

Type: Binary
URI: [http://akirad.cinelerra.org/](http://akirad.cinelerra.org/)
Distribution: akirad-intrepid
Components: main
Comment: Akirad Repository - Mirror1

Cinelerra does not appear in Synaptic. When trying to install using apt-get - I get the error:

```
Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  cinelerra: Depends: liblame0 (>= 3.96.1) but it is not installable
             Depends: libopenexr2c2a (>= 1.2.2) but it is not installable
             Depends: libquicktimehv (>= 1:2.1.0) but it is not going to be installed
             Depends: libquicktimehv (= 1:2.1.0-2svn20071122ubuntu1) but it is not going to be installed
E: Broken packages
```



I tried installing liblame0 seperately, but I get the error:

```
Package liblame0 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libmp3lame0
E: Package liblame0 has no installation candidate
```



Is it safe to perform a force install? Or better still is there a fixed package available anywhere? 

Thanks

---

### Post by bumanie on 2008-12-30
Hmm...not sure what to suggest. I managed to get cinelerra to work in either hardy or intrepid (can't quite remember which) for the first time ever. I followed the link you supplied. I  found it too complex for what I needed and installed lives instead. Unless you need to very complex editing, have a look at lives.

---

### Post by penguintutor on 2009-01-01
Thanks for the suggestion. I've just tried Lives (hadn't heard of it before). I'm not sure Lives quite fits with what I'm looking for.

I've tried kdenlive which seams to be quite good, but I'm also looking to see what else is available.

---

### Post by penguintutor on 2009-01-03
I have now installed Cinelerra, but I've had to use the [Heroine Warrior]("http://heroinewarrior.com/cinelerra.php") version rather than the community developed version.

Having tried a few different tools I think that kdenlive is going to be the best solution for my current requirements. I installed using the builder rather than the one in the Ubuntu repositories, which was fairly straight forward. See: [installing kdenlive on Ubuntu 8.10]("http://www.watkissonline.co.uk/wordpress/?p=879#kdenlive").

I'm still keeping an open mind and will be monitoring the progress of all the video editors on Linux. This is an exciting time for Video editing for Linux and I look forward to what the future brings.

---

### Post by alyosa2001 on 2009-01-29
try this page for lamelib0
[http://debian-multimedia.org/dists/stable/main/binary-i386/package/liblame0.php](http://debian-multimedia.org/dists/stable/main/binary-i386/package/liblame0.php)

---

### Post by GARoss on 2009-02-05
> **penguintutor said:**
> I have now installed Cinelerra, but I've had to use the [Heroine Warrior]("http://heroinewarrior.com/cinelerra.php") version rather than the community developed version.

Having tried a few different tools I think that kdenlive is going to be the best solution for my current requirements. I installed using the builder rather than the one in the Ubuntu repositories, which was fairly straight forward. See: [installing kdenlive on Ubuntu 8.10]("http://www.watkissonline.co.uk/wordpress/?p=879#kdenlive").

I'm still keeping an open mind and will be monitoring the progress of all the video editors on Linux. This is an exciting time for Video editing for Linux and I look forward to what the future brings.

Interesting! I've edited with Sony Vegas for years & would like to check Cinelerra out. I did try to install Vegas 64 & 32 bit versions with Wine but they failed. It has something to do with NetFrame location. 
My problem is I'm new to Ubuntu 8.1 (3 days) & not use to it yet. The heroinewarrior site says it's for v8.04. Will this work in 8.10? I need the 64 bit.
Thanks

---

