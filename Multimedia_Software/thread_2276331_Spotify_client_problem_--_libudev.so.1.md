---
title: "Spotify client problem -- libudev.so.1"
date: 2015-05-01
forum: Multimedia Software
---

### Post by MissMonicaE on 2015-05-01
Hi!

I'm trying to use Spotify's Linux client (64bit Ubuntu 12.04). I installed it from their repository as per their instructions. It used to work, and then at some point it just...stopped. When I click on the icon in Dash, Dash closes the way it does when a clicked-on program is about to open, but then nothing happens. When I try to run it from terminal, I get
```
spotify: error while loading shared libraries: libudev.so.1: cannot open shared object file: No such file or directory
```

I poked around, and many people suggested making a symlink between libudev.so.1 and libudev.so.0, but these suggestions were always followed by warning that this might cause unspecified terrible problems down the road, and anyway I don't know what that means. I have libudev.so.0 and libudev.so.0.13.0,  but not libudev.so.1.

Someone who had libudev.so.1 but not libudev.so.1 was advised to install the deb, which sure sounds like a good idea. I can find the deb for libudev.so.0 ([http://packages.ubuntu.com/precise/libudev0](http://packages.ubuntu.com/precise/libudev0)) and for libudev-dev ([http://packages.ubuntu.com/precise/admin/libudev-dev](http://packages.ubuntu.com/precise/admin/libudev-dev)), but not for .so.1. Another suggestion was to run
```
sudo apt-get install libudev0:i386
```
which I tried, whereupon I was told this was already the latest version. Just in case, I tried
```
sudo apt-get install libudev1:i386
```
and got
```
Package libudev1:i386 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libudev1:i386' has no installation candidate
```

What am I missing here? :(

---

### Post by mc4man on 2015-05-01
From the spotify help site is there any indication that 12.04 (libudev0) users can use the *latest packaged* spotify?
While the package itself allows either libudev0 or libudev1 to satisfy the install dependency it could be that the binary will only  link to libudev1 (libudev.so.1

you may see that with - 
```
ldd /opt/spotify/spotify-client/spotify |grep libudev
```
If that's the case then *that package* is no good for 12.04, should be fine in 14.04

(- if it would actually work with libudev0 (libudev.so.0) then a symlink would possibly solve but users of a prepackaged source shouldn't have to do that. There's a decent possibility that it will not work with the old libudev

---

### Post by MissMonicaE on 2015-05-01
Thanks! I ran that and got
```
 [COLOR=#ff0000]libudev[/COLOR].so.1 => not found
```
How should I proceed?

---

### Post by mc4man on 2015-05-01
You could - 
1. Try the symlink, if it works fine, if not then  remove it (the symlink & current installed spotify
2. Look in /var/cache/apt/archives for the previous spotify package. If it's there consider downgrading to it with dkpg
3. Complain to spotify dev's responsible for the package that one package doesn't suit all..

---

### Post by MissMonicaE on 2015-05-02
Unfortunately I purged the old version, but I symlinked the two and it seems to work. Thank you! In the meantime I'll complain, since .so.1 doesn't seem to exist for Precise, which after all is almost two years away from its EOL.

Many people have warned about symlinks--do you know what problems I should be looking out for?

Thanks again!

---

### Post by mc4man on 2015-05-02
> **MissMonicaE said:**
> Unfortunately I purged the old version, but I symlinked the two and it seems to work. Thank you! In the meantime I'll complain, since .so.1 doesn't seem to exist for Precise, which after all is almost two years away from its EOL.

Many people have warned about symlinks--do you know what problems I should be looking out for?

Thanks again!
It shouldn't be an issue unless you did a 12.04 to 14.04 upgrade. If doing that you'd want to remove the symlink first before upgrading  as 14.04 would be installing a real libudev.so.1 ect.

---

### Post by MissMonicaE on 2015-05-02
Thank you very much! I'll probably upgrade some time after final exams, haha. :)

---

