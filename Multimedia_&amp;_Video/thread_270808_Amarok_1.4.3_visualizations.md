---
title: "Amarok 1.4.3 visualizations"
date: 2006-10-03
forum: Multimedia &amp; Video
---

### Post by digitalchef on 2006-10-03
I have spent seveal hours looking for libvisual0.4-plugins. I know that alot of people are having problems getting amarok visualizations running .Sounds like gnome users are the ones having troubles getting them to work. I currently running gnome (unbuntu 6.0.6) i hope thats right, I dont have to much knowledge on trying to pull information to together and making it work. If anyone has solved this problem for gnome users plz reply back 

Thanks

---

### Post by mitch.c on 2006-10-03
> **digitalchef said:**
> I have spent seveal hours looking for libvisual0.4-plugins. I know that alot of people are having problems getting amarok visualizations running .Sounds like gnome users are the ones having troubles getting them to work. I currently running gnome (unbuntu 6.0.6) i hope thats right, I dont have to much knowledge on trying to pull information to together and making it work. If anyone has solved this problem for gnome users plz reply back 

Thanks
I've had absolutely no problems running visualizations with Amarok 1.4.3
```
sudo apt-get install libvisual-0.4-0 libvisual-0.4-plugins
```
Give it a try.

---

### Post by Aikon- on 2006-10-03
Having a similar problem... I get the following results when trying to install libvisual-0.4-plugins

```
$ sudo apt-get install libvisual-0.4-plugins
Reading package lists... Done
Building dependency tree... Done
Package libvisual-0.4-plugins is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libvisual-0.4-plugins has no installation candidate

```

Suggestions? Here's my sources.list (minus commented entries and irrelevant sources):


```
deb http://packages.freecontrib.org/plf/ dapper free non-free
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted multiverse
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://kubuntu.org/packages/amarok-latest dapper main
deb-src http://kubuntu.org/packages/amarok-latest dapper main

```

---

### Post by mitch.c on 2006-10-03
> **Aikon- said:**
> Having a similar problem... I get the following results when trying to install libvisual-0.4-plugins

```
$ sudo apt-get install libvisual-0.4-plugins
Reading package lists... Done
Building dependency tree... Done
Package libvisual-0.4-plugins is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libvisual-0.4-plugins has no installation candidate

```

Suggestions? [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) dapper main

I was trying to remember how I did this... it occurs to me I may have added the edgy main repository to install libvisual-0.4-plugins. I removed the edgy repo immediately after.

---

### Post by Aikon- on 2006-10-03
> **mitch.c said:**
> I was trying to remember how I did this... it occurs to me I may have added the edgy main repository to install libvisual-0.4-plugins. I removed the edgy repo immediately after.

which would be.. ?

---

### Post by kuja on 2006-10-03
I ran into a similar problem a while back:

I solved it by first updating to the 1.4.2, then to 1.4.3, if I remember right.

---

### Post by mitch.c on 2006-10-03
> **Aikon- said:**
> which would be.. ?
I took a look at the packages, try libvisual-0.4-plugins from the edgy universe repository, and libvisual-0.4-0 from dapper backports.
```
# /etc/apt/sources.list

# replace 'us' with your country code
deb http://us.archive.ubuntu.com/ubuntu edgy universe

# this may already exist in sources.list... don't duplicate
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports
```

Let me know if this works.

---

### Post by digitalchef on 2006-10-10
i have already updated to 1.4.3 . what seems to be the problem is i cant download libvisual0.4-plugins, for some reason i cant find it . I'm not quite sure what my regional code is so for > libvisual-0.4-plugins from the edgy universe repository

if somone could point in the dirction of that then i try it. i think i alread y have the backports one.

---

